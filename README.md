# Template -- HUB Typescript


## Setup

Durante o setup deste projeto, utilizamos as seguintes ferramentas:

- **Husky**: Husky é uma ferramenta que nos permite definir hooks Git personalizados. No nosso caso, usamos o Husky para configurar ganchos pré-commit, o que nos permite executar scripts automaticamente antes de cada confirmação de alterações no Git. Isso nos ajuda a manter a qualidade do código e evitar a inclusão de alterações com problemas.

- **Commitizen**: Commitizen é uma ferramenta que nos ajuda a criar mensagens de commit consistentes e semânticas. Ele nos guia por um processo interativo para criar mensagens de commit que seguem um formato específico. Isso é útil para garantir que nossos commits sejam claros e bem documentados, facilitando a colaboração e a manutenção do código.

- **ESLint**: ESLint é uma ferramenta de análise estática de código para identificar e relatar padrões problemáticos no código JavaScript. Configuramos o ESLint com um conjunto de regras personalizadas para garantir a consistência e a qualidade do nosso código. Ele nos ajuda a detectar erros comuns, como variáveis não utilizadas, uso incorreto de sintaxe e padrões de código não conformes.

Claro, aqui está uma descrição melhorada e expandida:

✨ **Instalando o ESLint**

ESLint é uma ferramenta de análise estática de código para identificar e relatar padrões problemáticos no código JavaScript. Siga os passos abaixo para instalar e configurar o ESLint:

```bash
# Instalando o ESLint
yarn add eslint -D

# Inicializando o ESLint (cria o arquivo de configuração .eslintrc.js)
yarn eslint --init
```

Após instalar e configurar o ESLint, você pode executá-lo manualmente ou integrá-lo com ferramentas como o Husky para garantir que as verificações de linting sejam realizadas antes de cada confirmação de alterações.


✨ **Instalando o Husky**

Husky é uma ferramenta que nos permite definir ganchos Git personalizados para automatizar tarefas antes de cada confirmação de alterações. Siga os passos abaixo para instalar e configurar o Husky:

```bash
# Instalando Husky v6
yarn add husky -D

# Ativando os hooks
yarn husky install

# Adicionando hooks automaticamente após a instalação
"scripts": {
  "prepare": "husky install"
}

# Adicionando hook para disparar. Vá no arquivo pre-commit dentro da pasta husky e cole o codigo abaixo
```bash
#!/usr/bin/env sh
. "$(dirname -- "$0")/_/husky.sh"

npx eslint src/**/*.ts;
```

É essencial criar o script de `prepare` no arquivo `package.json` para automatizar a instalação do Husky. Isso garante que os ganchos sejam ativados automaticamente após a instalação, evitando a necessidade de configurá-los manualmente.

Após configurar o Husky, você pode testar se tudo está funcionando corretamente executando um commit.

```bash
# Adicionando arquivos para serem commitados
git add .

# Fazendo um commit para testar a configuração
git commit -m "chore: add e husky"
```

✨ **Instalando o Commitizen**

Commitizen é uma ferramenta que nos ajuda a criar mensagens de commit consistentes e semânticas. Siga os passos abaixo para instalar e configurar o Commitizen:

```bash
# Instalando o Commitizen
yarn add commitizen -D

# Criando a configuração
yarn commitizen init cz-conventional-changelog --yarn --dev --exact

# Adicionando um script no package.json para iniciar o Commitizen
"scripts": {
  "commit": "git-cz"
}
```

Após instalar e configurar o Commitizen, você pode fazer um commit usando o seguinte comando:

```bash
# Adicionando arquivos para serem commitados
git add .

# Iniciando o Commitizen para fazer um commit
yarn commit
```

Template bacana para iniciar um projeto em typescript

No final adicione esse debug, isso vai ficar 100% automatizado

```bash
  "scripts": {
    "start:dev": " tsx src/app.ts --watch",
    "start": "tsx dist/app.js",
    "build": "tsc",
    "prepare": "husky install",
    "lint": "eslint src/**/*.ts",
    "commit": "git-cz",
    "git": "git add . && npm run lint && npm run commit && git push origin HEAD"
  },

```

