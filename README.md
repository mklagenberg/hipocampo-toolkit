# hipocampo-toolkit

Template e skill pra instanciar a metodologia [Hipocampo](https://github.com/mklagenberg/hipocampo) em qualquer git host.

## Como usar

1. Clique em **"Use this template"** neste repositório para criar seu repositório de conteúdo.
2. Siga o checklist completo em **[POS-INSTANCIACAO.md](POS-INSTANCIACAO.md)** — o template só copia um esqueleto; marcar como privado, trocar o LICENSE e instalar a skill personalizada são passos obrigatórios, não opcionais.

Guia completo de adoção (incluindo ordem de leitura pra quem está aprendendo a metodologia pela primeira vez): [hipocampo/GETTING-STARTED.md](https://github.com/mklagenberg/hipocampo/blob/main/GETTING-STARTED.md).

## O que tem aqui

- `CLAUDE.md` — instrução pro agente de IA operar essa instância, com o bloco de extensões locais pronto pra preencher.
- `POS-INSTANCIACAO.md` — checklist de primeira configuração depois de instanciar.
- `license-templates/` — templates de LICENSE pros perfis pessoal e corporativo, pra substituir o Apache-2.0 herdado indevidamente.
- `registry.md` — tabela vazia pra registrar aliases de `related` cross-repositório (ver `hipocampo/SPEC.md`, seção 6).
- `example/exemplo-nota.md` — documento de exemplo com frontmatter completo.
- `skill/SKILL.md` — skill genérica e portável da metodologia: ritual REM, staleness, resolução de `related`, mecânica CRUD/frontmatter-first, checagem de release nova. Precisa ser personalizada (roteador de repositórios) antes de uso real — ver `POS-INSTANCIACAO.md`.

Versão do Hipocampo referenciada por este template: **^1.7.0**.
