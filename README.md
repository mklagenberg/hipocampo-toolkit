# hipocampo-toolkit

Template e stub de skill pra instanciar a metodologia [Hipocampo](https://github.com/mklagenberg/hipocampo) em qualquer git host.

## Como usar

1. Clique em **"Use this template"** neste repositório para criar seu repositório de conteúdo.
2. **Marque o repositório novo como privado.** Não é opcional — é invariante da metodologia (ver `hipocampo/SPEC.md`, seção 8).
3. Abra `CLAUDE.md` no repositório novo e preencha o bloco "Extensões locais a Hipocampo vX.Y" com as decisões específicas da sua instância.
4. Apague ou adapte o exemplo em `example/exemplo-nota.md` — ele existe só pra ilustrar o frontmatter, não é conteúdo real.

Guia completo de adoção: [hipocampo/GETTING-STARTED.md](https://github.com/mklagenberg/hipocampo/blob/main/GETTING-STARTED.md).

## O que tem aqui

- `CLAUDE.md` — instrução pro agente de IA operar essa instância, com o bloco de extensões locais pronto pra preencher.
- `registry.md` — tabela vazia pra registrar aliases de `related` cross-repositório (ver `hipocampo/SPEC.md`, seção 6).
- `example/exemplo-nota.md` — documento de exemplo com frontmatter completo.
- `skill/` — stub. A arquitetura da(s) skill(s) do toolkit ainda está em aberto (decisão adiada, ver `hipocampo` `decisions/`) — este arquivo é só um placeholder documentando o que falta.

Versão do Hipocampo referenciada por este template: **^1.0.0**.
