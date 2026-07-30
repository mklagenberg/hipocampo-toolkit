# CLAUDE.md — instância Hipocampo

Este arquivo instrui um agente de IA (Claude ou equivalente) sobre como operar este repositório como uma instância da metodologia [Hipocampo](https://github.com/mklagenberg/hipocampo).

**Versão do Hipocampo seguida por esta instância:** ^1.9.0

## Invariantes (nunca sobrescrever)

1. Este repositório nunca é tornado público.
2. `author` é sempre uma pessoa, nunca a IA.
3. Documento nunca é apagado fisicamente — só arquivado (`status: archived`) ou substituído (`status: superseded`, com `superseded_by` preenchido). Exceção estreita: apagamento por obrigação legal de eliminação de dado pessoal, sempre com decisão humana explícita (ver `hipocampo/decisions/0010`).
4. Nunca escrever, editar ou apagar conteúdo sem pedido explícito do usuário nesta conversa.

Detalhe completo dos invariantes: `hipocampo/SPEC.md`, seção 8.

## Antes de usar este template

Siga `POS-INSTANCIACAO.md` — checklist obrigatório: privacidade do repositório, troca de `LICENSE`, personalização e instalação da skill (`skill/SKILL.md`), preenchimento deste arquivo, declaração de versão.

## Extensões locais a Hipocampo v1.9.0

<!-- Preencher ao instanciar. Documentar aqui qualquer ajuste específico desta instância — nunca deixar implícito. -->

- **Subpastas de `category` já em uso:** (nenhuma ainda)
- **`ttl` default sugerido por tipo de conteúdo:** (usar sugestões do SPEC.md, seção 5, até haver motivo pra desviar)
- **Rituais extras específicos:** (nenhum ainda)
- **Nomenclatura de commit/branch:** (usar convenção default até haver motivo pra desviar)

## Frontmatter — referência rápida

Ver o schema completo em `hipocampo/SPEC.md`, seção 2. Resumo dos campos obrigatórios em todo documento novo: `title`, `date`, `updated`, `source`, `type`, `temporality`, `ttl`, `status`, `visibility`, `author`, `revision`.

Ao operar sobre múltiplos documentos (busca, triagem, staleness), leia o frontmatter primeiro — é suficiente pra filtrar relevância na maioria dos casos — e só leia o corpo completo do documento depois de decidir que aquele documento específico precisa (mecânica CRUD/frontmatter-first, `hipocampo/SPEC.md`, seção 2-B).

## Referências cross-repositório

Se esta instância referencia ou é referenciada por outro repositório Hipocampo, registrar o alias em `registry.md` (nunca editar linha existente — só acrescentar).
