# Pós-instanciação — checklist de primeira configuração

Você acabou de clicar em "Use this template" e tem um repositório novo. Ele **não** está pronto pra uso ainda — o template só copia um esqueleto. Faça os passos abaixo, nesta ordem, antes de guardar qualquer conhecimento real.

## 1. Marque o repositório como privado

Não é opcional. É o invariante que sustenta todo o modelo de `visibility` da metodologia (`hipocampo/SPEC.md`, seção 8, invariante 1).

## 2. Substitua o LICENSE

O template copiou o Apache-2.0 da metodologia — **errado para um repositório de conteúdo**, mesmo privado, porque o texto da licença em si já afirmaria uma permissão de uso que não é sua intenção.

1. Abra `license-templates/README.md` e escolha o template certo (pessoal ou corporativo).
2. Preencha os placeholders (nome/handle, ou razão social).
3. Se este repositório for de nível "vault" (só recebe `visibility: confidential`/`restricted`), siga a nota de ajuste dentro do próprio template.
4. Salve o resultado como `LICENSE` na raiz, substituindo o Apache-2.0 herdado.

## 3. Apague a pasta `skill/` herdada e instale a skill de verdade

A pasta `skill/` que veio junto com "Use this template" é resíduo do mecanismo de cópia do GitHub — **não é uma cópia funcional da skill**, nunca foi, e este repositório de conteúdo não deveria carregar uma. A skill roda sempre no seu ambiente de IA (Cowork, Claude Code, etc.), por pessoa, nunca por repositório — nenhum agente varre repositórios do GitHub procurando um `SKILL.md` pra ativar automaticamente (ver `hipocampo/decisions/0025-skill-client-side-nunca-por-repositorio.md`).

1. **Apague a pasta `skill/` deste repositório recém-instanciado.** Ela não faz falta — editar os arquivos dentro dela nunca teve efeito nenhum.
2. Vá direto em [`hipocampo-toolkit/skill/SKILL.md`](skill/SKILL.md) + `skill/references/*.md` (aqui no toolkit, a fonte canônica) e instale sua própria cópia personalizada no seu ambiente de IA (ex.: via `save_skill`, ou o mecanismo equivalente da ferramenta que você usa).
3. Preencha a tabela de roteador de repositórios em `references/personalizacao.md` da sua cópia, incluindo **este repositório novo** — junto com os demais que você já opera.
4. Se você operar mais de uma conta de git que resolvem pro mesmo autor humano (ex.: pessoal e vinculada a empregador), preencha também a tabela de identidade multi-conta no mesmo arquivo — só na sua cópia pessoal, nunca na genérica (`hipocampo/SPEC.md`, seção 12).

Sem este passo, você tem o texto da skill guardado em arquivos no toolkit, mas nenhum agente vai realmente segui-la — e continuar com a pasta `skill/` dentro deste repositório só mantém viva a ideia errada de que ela faz alguma coisa aqui.

## 4. Preencha o AGENTS.md

`AGENTS.md` é o arquivo canônico de instrução desta instância (`CLAUDE.md` é só um ponteiro fino pra ele — não precisa editar o `CLAUDE.md`). Abra `AGENTS.md` e preencha:

- **Escopo deste repositório** — dois campos obrigatórios: o **tipo de instância** (`corporativa` ou `pessoal`, usado pela auditoria estrutural pra saber qual variante da política de dados sensíveis aplicar) e o que deve/não deve ser armazenado aqui, e pra onde vai o que não pertence. Nunca deixar implícito.
- **Identidade de autor multi-conta**, se aplicável (mesma nota do passo 3 — só se você usar mais de uma conta de git).
- **Extensões locais a Hipocampo vX.Y** — subpastas de `category` que você já sabe que vai usar, `ttl` default por tipo de conteúdo, rituais extras, convenção de commit/branch. Se não houver nada pra declarar ainda, deixe registrado como "nenhum ainda", não em branco.
- **Rituais de manutenção** — confirme a cadência (default: frontmatter audit + REM diários, auditoria estrutural semanal) ou registre o ajuste real desta instância.

## 5. Declare a versão de compatibilidade

No mesmo `AGENTS.md`, confirme a linha "Versão do Hipocampo seguida por esta instância" — deve refletir a versão atual do `hipocampo/SPEC.md` no momento da instanciação, não um valor copiado sem checar.

## 6. Apague ou adapte o exemplo

`example/exemplo-nota.md` existe só pra ilustrar o frontmatter — não é conteúdo real. Apague ou adapte antes do primeiro documento de verdade.

## Pronto

A partir daqui, siga `hipocampo/GETTING-STARTED.md` (seções 3 em diante) pra escrever seu primeiro documento e configurar as rotinas (frontmatter audit, REM, auditoria estrutural), já cobertas pela skill que você acabou de personalizar.
