# Templates de LICENSE — leia antes de instanciar

Quando você cria um repositório de conteúdo a partir deste template ("Use this template"), o GitHub copia o arquivo `LICENSE` da raiz — que aqui é a licença Apache-2.0 da **metodologia** (correta para `hipocampo`/`hipocampo-toolkit`, errada para o seu repositório de conteúdo).

**Seu repositório de conteúdo nunca deve ficar com essa licença.** Conteúdo é sempre proprietário/confidencial, nunca aberto (ver `hipocampo/decisions/0007-licenciamento-repos-de-conteudo.md`) — isso vale mesmo que o repositório seja privado, porque o texto da LICENSE em si já afirmaria uma permissão de uso que não é sua intenção.

## O que fazer

1. Escolha o template certo pelo titular do conteúdo:
   - **`LICENSE-pessoal.md`** — se o titular é uma pessoa física (`hipocampo-concepts`, `hipocampo-personal-vault` ou equivalente).
   - **`LICENSE-corporativo.md`** — se o titular é uma empresa (`hipocampo-company`, `hipocampo-company-vault` ou equivalente).
2. Preencha os placeholders (`[NOME COMPLETO]`/`[@usuario-github]` ou `[NOME DA EMPRESA]`).
3. Se o repositório for de nível "vault" (só recebe `visibility: confidential`/`restricted`, nunca `public`/`internal` — ver `hipocampo/SPEC.md`, seção 2), mantenha só as seções (c) e (d) do template e ajuste o parágrafo de abertura para mencionar que é a contraparte "vault" do repositório principal, seguindo o padrão já em uso em `hipocampo-company-vault/LICENSE`.
4. Salve o resultado como `LICENSE` na raiz do seu repositório, substituindo o Apache-2.0 herdado.

Este passo é parte obrigatória da rotina de pós-instanciação — não é opcional nem cosmético: sem ele, seu repositório de conteúdo privado carrega, tecnicamente, uma licença de código aberto.
