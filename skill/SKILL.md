---
name: hipocampo
description: >
  Opera uma instância da metodologia Hipocampo (second brain agêntico: git + markdown
  + rituais de IA) através do MCP do GitHub. Use sempre que o usuário pedir para
  consultar, salvar, registrar, atualizar, arquivar ou organizar conhecimento em
  qualquer repositório Hipocampo — pessoal ou corporativo —, ao rodar o ritual REM
  (consolidação de inbox), ao rodar a checagem de staleness, ou ao resolver uma
  referência cross-repositório (`$alias:path.md`). Também ativa no início de uma
  sessão para checar se há uma versão nova da metodologia publicada no repositório
  `hipocampo` e avisar o usuário. Template genérico — não hardcoda nome de nenhum
  repositório pessoal ou corporativo; ver seção "Personalização obrigatória" abaixo.
---

# Skill Hipocampo

Esta skill opera qualquer instância da metodologia [Hipocampo](https://github.com/mklagenberg/hipocampo) via GitHub MCP. Ela é publicada como template genérico em `hipocampo-toolkit/skill/SKILL.md` — **nunca deve ser usada assim, sem personalização** (ver seção abaixo). Ela substitui o antigo `skill/SKILL-STUB.md`, que só registrava o escopo pendente.

## Personalização obrigatória — leia antes de usar

Esta cópia genérica só conhece dois repositórios, universais para qualquer usuário:

- `mklagenberg/hipocampo` — spec da metodologia.
- `mklagenberg/hipocampo-toolkit` — template e ferramental.

Ela **não** conhece nenhum repositório pessoal ou corporativo — isso variaria por usuário/empresa, e hardcodar quebraria a possibilidade de qualquer pessoa ou empresa adotar esta mesma skill. Antes de usar de verdade, quem adota a metodologia deve salvar sua própria cópia personalizada desta skill (ex.: via `save_skill`), preenchendo a tabela abaixo com os repositórios da própria instância:

```
| Papel                        | Repositório                          |
|-------------------------------|---------------------------------------|
| Conceitos pessoais (público*) | [preencher: owner/repo]               |
| Vault pessoal                 | [preencher: owner/repo]               |
| Conteúdo corporativo           | [preencher: owner/repo]               |
| Vault corporativo              | [preencher: owner/repo]               |

* "público" aqui é só no sentido de "menos restrito dentro do escopo pessoal" —
  nenhum repositório de conteúdo é público à internet (invariante 1, SPEC.md §8).
```

Nem toda instância tem os quatro — preencher só o que existir. Este é o "roteador" de repositórios desta instância; sem ele preenchido, a skill não sabe onde ler/escrever conhecimento além da própria metodologia.

## Checagem de release nova (início de sessão)

No início de uma sessão, ou quando o usuário pedir, comparar a versão declarada no `CLAUDE.md` desta instância ("Versão do Hipocampo seguida: ^X.Y.Z") contra a versão atual publicada em `mklagenberg/hipocampo/SPEC.md`. Se houver diferença:

1. Avisar o usuário explicitamente, citando as duas versões.
2. Resumir o que mudou (via `CHANGELOG.md` do `hipocampo`, entradas entre a versão declarada e a atual).
3. Nunca aplicar a atualização sozinha — apontar a decisão de migrar (ou não) para o usuário, e referenciar `MIGRATIONS.md` se a mudança for MAJOR (ver `decisions/0014-rotina-obrigatoria-de-release.md`).

## Mecânica CRUD e leitura frontmatter-first

Ao operar sobre múltiplos documentos (busca, triagem, staleness), ler sempre o frontmatter primeiro — é suficiente pra filtrar por `type`, `tags`, `status`, `temporality`, `related` na maioria dos casos. Só ler o corpo completo depois de decidir, pelo frontmatter, que aquele documento específico precisa (SPEC.md, seção 2-B). Não ler o corpo inteiro de todo documento candidato como padrão — é desperdício de token evitável.

## Ritual REM (consolidação de inbox)

Lê só da pasta `inbox/` do repositório relevante (memória de curto prazo), nunca direto da conversa atual (memória sensorial — SPEC.md, seção 5-A). Para cada item pendente: decidir entre virar documento novo, fundir com um existente, ou descartar. **Sempre apresentar o plano completo antes de qualquer escrita** — mesmo invariante de pedido explícito (SPEC.md, seção 8) aplicado a este ritual. Só executar depois de confirmação humana.

## Ritual de staleness

Verificar documentos com `ttl` vencido, tratando cada um conforme `temporality` (SPEC.md, seção 5): `evergreen` recebe checagem leve ("ainda é verdade?"); `ephemeral` vencido sem renovação já é candidato a `archived`/`superseded`, não só "revisar"; `contextual` é checado também pelo status do documento em `context_anchor`, independente do `ttl`; `historical` é pulado por completo. Sempre apresentar os achados antes de alterar `status` de qualquer documento — mesmo invariante de pedido explícito.

## Resolução de `related` cross-repositório

Quando um documento referencia `$alias:path.md`, resolver o alias consultando o `registry.md` do repositório menos restrito do escopo relevante (SPEC.md, seção 6). Nunca editar uma linha existente do registry ao encontrar um repositório renomeado — sempre acrescentar linha nova, preservando a antiga.

## Invariantes (nunca sobrescrever, em nenhuma instância)

1. Nenhum repositório de conhecimento é público à internet.
2. `author` é sempre uma pessoa, nunca a IA.
3. Documento nunca é apagado fisicamente — só arquivado ou superseded (exceção estreita: `decisions/0010`, sempre com decisão humana explícita).
4. Separação de acesso é sempre por repositório, nunca por etiqueta dentro de um repositório compartilhado.
5. O agente nunca escreve, edita ou apaga conteúdo sem pedido explícito do usuário na conversa atual.

Detalhe completo: `hipocampo/SPEC.md`, seção 8.
