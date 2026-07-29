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

## 3. Personalize e instale sua própria cópia da skill

`skill/SKILL.md` é genérica — hardcoda só os dois repositórios universais da metodologia (`hipocampo`, `hipocampo-toolkit`). Ela não sabe nada sobre os seus repositórios pessoais/corporativos até você preencher o roteador.

1. Copie `skill/SKILL.md` pra sua própria skill personalizada (não edite o arquivo dentro do repositório de conteúdo como se isso já a ativasse — skills vivem no seu ambiente de IA, não no repositório).
2. Preencha a tabela "Personalização obrigatória" com os repositórios reais da sua instância (conceitos pessoais, vault pessoal, conteúdo corporativo, vault corporativo — só o que existir).
3. Registre a skill de fato no seu ambiente (ex.: via `save_skill`, ou o mecanismo equivalente da ferramenta que você usa).

Sem este passo, você tem o texto da skill guardado num arquivo, mas nenhum agente vai realmente segui-la.

## 4. Preencha o CLAUDE.md

Abra `CLAUDE.md` e preencha o bloco "Extensões locais a Hipocampo vX.Y": subpastas de `category` que você já sabe que vai usar, `ttl` default por tipo de conteúdo, rituais extras, convenção de commit/branch. Nunca deixar implícito — se não houver nada pra declarar ainda, deixe registrado como "nenhum ainda", não em branco.

## 5. Declare a versão de compatibilidade

No mesmo `CLAUDE.md`, confirme a linha "Versão do Hipocampo seguida por esta instância" — deve refletir a versão atual do `hipocampo/SPEC.md` no momento da instanciação, não um valor copiado sem checar.

## 6. Apague ou adapte o exemplo

`example/exemplo-nota.md` existe só pra ilustrar o frontmatter — não é conteúdo real. Apague ou adapte antes do primeiro documento de verdade.

## Pronto

A partir daqui, siga `hipocampo/GETTING-STARTED.md` (seções 3 em diante) pra escrever seu primeiro documento e configurar as rotinas (staleness, consolidação REM), já cobertas pela skill que você acabou de personalizar.
