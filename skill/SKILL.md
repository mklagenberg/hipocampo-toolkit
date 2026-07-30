---
name: hipocampo
description: >
  Opera uma instância da metodologia Hipocampo (second brain agêntico: git + markdown
  + rituais de IA) através do MCP do GitHub. Use sempre que o usuário pedir para
  consultar, salvar, registrar, atualizar, arquivar ou organizar conhecimento em
  qualquer repositório Hipocampo — pessoal ou corporativo —, ao rodar o frontmatter
  audit, o ritual REM (consolidação de inbox), a auditoria estrutural semanal, ou ao
  resolver uma referência cross-repositório (`$alias:path.md`). Também ativa no
  início de uma sessão para checar se há uma versão nova da metodologia publicada no
  repositório `hipocampo` e avisar o usuário. Template genérico — não hardcoda nome
  de nenhum repositório pessoal ou corporativo; ver seção "Personalização
  obrigatória" abaixo.
---

# Skill Hipocampo

Esta skill opera qualquer instância da metodologia [Hipocampo](https://github.com/mklagenberg/hipocampo) via GitHub MCP. Ela é publicada como template genérico em `hipocampo-toolkit/skill/SKILL.md` — **nunca deve ser usada assim, sem personalização** (ver seção abaixo).

**Versão do Hipocampo que esta cópia da skill segue:** ^1.9.0 (mais os itens de `CHANGELOG.md` `[Não lançado]` no momento da última sincronização desta skill — frontmatter audit, auditoria estrutural, AGENTS.md, identidade multi-conta). Ao personalizar sua cópia, confirme se ainda bate com o `AGENTS.md` da sua instância.

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

### Identidade de autor multi-conta (preencher se aplicável)

Se você opera mais de uma conta de git que representam o mesmo `author` humano (ex.: pessoal e vinculada a empregador):

```
| Conta de git         | Papel                     |
|-----------------------|----------------------------|
| [preencher: @handle]  | Pessoal                    |
| [preencher: @handle]  | Profissional/corporativo   |
```

Nunca preencher isso na cópia genérica do template — só na sua cópia pessoal. Direção de convite entre instância pessoal e corporativa: a conta pessoal sempre convida a profissional pro second brain **pessoal**, nunca o inverso (`hipocampo/SPEC.md`, seção 12; `hipocampo/decisions/0020-identidade-autor-multi-conta.md`).

## Checagem de release nova (início de sessão)

No início de uma sessão, ou quando o usuário pedir, comparar a versão declarada no `AGENTS.md` desta instância ("Versão do Hipocampo seguida: ^X.Y.Z") contra a versão atual publicada em `mklagenberg/hipocampo/SPEC.md`. Se houver diferença:

1. Avisar o usuário explicitamente, citando as duas versões.
2. Resumir o que mudou (via `CHANGELOG.md` do `hipocampo`, entradas entre a versão declarada e a atual — incluindo a seção `[Não lançado]`, se houver).
3. Nunca aplicar a atualização sozinha — apontar a decisão de migrar (ou não) para o usuário, e referenciar `MIGRATIONS.md` se a mudança for MAJOR (ver `decisions/0014-rotina-obrigatoria-de-release.md`).

## Mecânica CRUD, leitura frontmatter-first e validação em tempo de leitura

Ao operar sobre múltiplos documentos (busca, triagem, staleness), ler sempre o frontmatter primeiro — é suficiente pra filtrar por `type`, `tags`, `status`, `temporality`, `related` na maioria dos casos. Só ler o corpo completo depois de decidir, pelo frontmatter, que aquele documento específico precisa (SPEC.md, seção 2-B). Não ler o corpo inteiro de todo documento candidato como padrão — é desperdício de token evitável.

Além disso, toda leitura valida o frontmatter contra a norma (SPEC.md, seção 2) e a checagem de staleness (seção 5), independente de o frontmatter audit já ter passado por aquele documento. Se algo estiver errado, sinalizar explicitamente o quê e o que fazer — no caso de `ttl` vencido, deixar claro que a informação é defasada e sugerir revalidação por pesquisa quando o documento for `source: url` (mesmo mecanismo da skill `deep-research`, acionado aqui também por este gatilho). Nunca alterar `status` ou qualquer campo sozinho — só sinalizar (SPEC.md, seção 2-B; `decisions/0018-validacao-frontmatter-tempo-de-leitura.md`).

## Frontmatter audit (ritual determinístico, cadência diária)

Varredura mecânica — não julgamento de agente — do frontmatter de todo documento de um repositório: `ttl` vencido, campo obrigatório ausente, outra violação detectável da norma. Produz/atualiza `meta/fila-de-manutencao.md` daquele repositório. Nunca decide disposição, só relata. Roda antes do ritual REM do mesmo ciclo (SPEC.md, seção 5-B; `decisions/0017-frontmatter-audit-ritual-deterministico.md`).

## Ritual REM (consolidação de inbox + atualização de memórias antigas, cadência diária)

Duas funções, sempre no escopo de um repositório por vez:

1. **Consolidar** — ler `inbox/` (memória de curto prazo — sanitização, não só captura bruta), decidir por item entre virar documento novo, fundir com um existente, ou descartar.
2. **Atualizar memórias antigas** — ler `meta/fila-de-manutencao.md` (produzida pelo frontmatter audit) e decidir disposição de cada pendência: revalidar, arquivar, superseder, corrigir campo.

**Sempre apresentar o plano completo antes de qualquer escrita**, pras duas funções — mesmo invariante de pedido explícito (SPEC.md, seção 8) aplicado a este ritual. Só executar depois de confirmação humana (SPEC.md, seção 5-A; `decisions/0016-memoria-curto-prazo-sanitizacao.md`).

## Auditoria estrutural (cadência semanal)

Três funções: atomicidade dos documentos já consolidados, posicionamento (a estrutura de `category`/pastas ainda faz sentido? algo está fora do escopo declarado no `AGENTS.md` deste repositório?), e verificação de vazamento de dado sensível contra a política por tipo de instância (SPEC.md, seção 2-A). Qualquer achado é sempre apresentado ao humano antes de qualquer ação — mover, dividir ou remover documento nunca acontece sozinho (SPEC.md, seção 5-C; `decisions/0019-auditoria-estrutural-semanal.md`).

## Resolução de `related` cross-repositório

Quando um documento referencia `$alias:path.md`, resolver o alias consultando o `registry.md` do repositório menos restrito do escopo relevante (SPEC.md, seção 6). Nunca editar uma linha existente do registry ao encontrar um repositório renomeado — sempre acrescentar linha nova, preservando a antiga.

## Invariantes (nunca sobrescrever, em nenhuma instância)

1. Nenhum repositório de conhecimento é público à internet.
2. `author` é sempre uma pessoa, nunca a IA.
3. Documento nunca é apagado fisicamente — só arquivado ou superseded (exceção estreita: `decisions/0010`, sempre com decisão humana explícita).
4. Separação de acesso é sempre por repositório, nunca por etiqueta dentro de um repositório compartilhado.
5. O agente nunca escreve, edita ou apaga conteúdo sem pedido explícito do usuário na conversa atual.

Detalhe completo: `hipocampo/SPEC.md`, seção 8.
