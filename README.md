# hipocampo-toolkit

Template e skill pra instanciar a metodologia [Hipocampo](https://github.com/mklagenberg/hipocampo) em qualquer git host.

## Como usar

1. Clique em **"Use this template"** neste repositório para criar seu repositório de conteúdo.
2. Siga o checklist completo em **[POS-INSTANCIACAO.md](POS-INSTANCIACAO.md)** — o template só copia um esqueleto; marcar como privado, trocar o LICENSE e instalar a skill personalizada são passos obrigatórios, não opcionais.

Guia completo de adoção (incluindo ordem de leitura pra quem está aprendendo a metodologia pela primeira vez): [hipocampo/GETTING-STARTED.md](https://github.com/mklagenberg/hipocampo/blob/main/GETTING-STARTED.md).

## O que tem aqui

- `AGENTS.md` — arquivo canônico de instrução pro agente de IA operar essa instância (qualquer ferramenta, não só Claude), com os blocos de escopo do repositório (incluindo o tipo de instância, corporativa ou pessoal), identidade multi-conta e extensões locais prontos pra preencher.
- `CLAUDE.md` — ponteiro fino pra `AGENTS.md`, só porque Claude Code/Cowork procuram por este nome especificamente.
- `POS-INSTANCIACAO.md` — checklist de primeira configuração depois de instanciar.
- `license-templates/` — templates de LICENSE pros perfis pessoal e corporativo, pra substituir o Apache-2.0 herdado indevidamente.
- `registry.md` — tabela vazia pra registrar aliases de `related` cross-repositório (ver `hipocampo/SPEC.md`, seção 6).
- `example/exemplo-nota.md` — documento de exemplo com frontmatter completo.
- `skill/` — skill genérica e portável da metodologia, em duas camadas: `SKILL.md` é o roteador enxuto (gatilhos e quando agir); `references/*.md` traz o procedimento completo de cada mecanismo (rotinas de manutenção, CRUD/frontmatter, personalização/identidade, invariantes), carregado sob demanda. Precisa ser personalizada (roteador de repositórios e identidade, em `references/personalizacao.md`) antes de uso real — ver `POS-INSTANCIACAO.md`.

Versão do Hipocampo referenciada por este template: **^1.9.0 + não lançado** — ver `hipocampo/CHANGELOG.md`, seção `[Não lançado]`, pra saber exatamente o que isso inclui além da última release formal.
