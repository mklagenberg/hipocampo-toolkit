# AGENTS.md — instância Hipocampo

Este é o arquivo canônico de instrução operacional desta instância da metodologia [Hipocampo](https://github.com/mklagenberg/hipocampo) — segue o padrão aberto [AGENTS.md](https://agents.md), funciona com qualquer agente de IA, não só Claude (ver `hipocampo/decisions/0015-agents-md-arquivo-canonico-instrucao.md`). `CLAUDE.md`, neste repositório, é só um ponteiro fino pra este arquivo.

**Versão do Hipocampo seguida por esta instância:** ^1.9.0 + não lançado (este template já reflete conteúdo mesclado em `hipocampo`@main além da última release formal — ver `hipocampo/CHANGELOG.md`, seção `[Não lançado]`, e `hipocampo/decisions/0021-politica-de-cadencia-de-release.md`)

## Invariantes (nunca sobrescrever)

1. Este repositório nunca é tornado público.
2. `author` é sempre uma pessoa, nunca a IA.
3. Documento nunca é apagado fisicamente — só arquivado (`status: archived`) ou substituído (`status: superseded`, com `superseded_by` preenchido). Exceção estreita: apagamento por obrigação legal de eliminação de dado pessoal, sempre com decisão humana explícita (ver `hipocampo/decisions/0010`).
4. Separação de acesso é sempre por repositório, nunca por etiqueta dentro de um repositório compartilhado.
5. Nunca escrever, editar ou apagar conteúdo sem pedido explícito do usuário nesta conversa.

Detalhe completo dos invariantes: `hipocampo/SPEC.md`, seção 8.

## Antes de usar este template

Siga `POS-INSTANCIACAO.md` — checklist obrigatório: privacidade do repositório, troca de `LICENSE`, personalização e instalação da skill (`skill/SKILL.md`), preenchimento deste arquivo, declaração de versão.

## Escopo deste repositório

<!-- Preencher ao instanciar: o que deve e o que não deve ser armazenado aqui, e pra onde vai o que não pertence. Nunca deixar implícito — é a fonte que os rituais de manutenção (REM, auditoria estrutural) consultam pra decidir se um documento pertence a este repositório (hipocampo/SPEC.md, seção 11). -->

(nenhuma definição ainda — preencher ao instanciar, antes do primeiro documento real)

## Identidade de autor multi-conta

<!-- Preencher só se você operar mais de uma conta de git que resolvem pro mesmo autor humano (ex.: pessoal e vinculada a empregador). Nunca preencher isso no hipocampo/hipocampo-toolkit públicos — só na sua instância pessoal. Ver hipocampo/SPEC.md, seção 12. -->

(nenhuma ainda)

## Extensões locais a Hipocampo v1.9.0

<!-- Preencher ao instanciar. Documentar aqui qualquer ajuste específico desta instância — nunca deixar implícito. -->

- **Subpastas de `category` já em uso:** (nenhuma ainda)
- **`ttl` default sugerido por tipo de conteúdo:** (usar sugestões do SPEC.md, seção 5, até haver motivo pra desviar)
- **Rituais extras específicos:** (nenhum ainda)
- **Nomenclatura de commit/branch:** (usar convenção default até haver motivo pra desviar)

## Rituais de manutenção

Cadência recomendada pela metodologia (`hipocampo/SPEC.md`, seções 5-A a 5-C): frontmatter audit e ritual REM diários (audit sempre antes da REM, no mesmo ciclo); auditoria estrutural semanal (atomicidade, posicionamento, verificação de dado sensível). Preencher aqui se a cadência real desta instância difere da recomendação, ou se algum ritual já está automatizado (ex.: scheduled task).

- **Cadência real:** (default da metodologia, nenhum ajuste ainda)

## Frontmatter — referência rápida

Ver o schema completo em `hipocampo/SPEC.md`, seção 2. Resumo dos campos obrigatórios em todo documento novo: `title`, `date`, `updated`, `source`, `type`, `temporality`, `ttl`, `status`, `visibility`, `author`, `revision`.

Toda leitura (READ) valida o frontmatter contra a norma e sinaliza problema — incluindo `ttl` vencido, com sugestão de revalidação por pesquisa quando aplicável (mecânica CRUD/frontmatter-first estendida, `hipocampo/SPEC.md`, seção 2-B).

## Referências cross-repositório

Se esta instância referencia ou é referenciada por outro repositório Hipocampo, registrar o alias em `registry.md` (nunca editar linha existente — só acrescentar).
