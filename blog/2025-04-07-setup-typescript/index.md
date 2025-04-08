---
slug: como-fazer-setup-do-typescript-com-nodejs
title: Como fazer o setup do typescript com NodeJS
authors: [devluar]
tags: [typescript]
---

Fala devs! Nesse breve post vou te fornecer os passos para iniciar seu projeto Typescript + NodeJS!

Requisitos:
- NodeJS instalado (e npm em unix)
- Editor de código com terminal integrado (Ex: [Visual Studio Code](https://code.visualstudio.com))

## Criação da pasta e navegação

Crie uma pasta para o projeto no local que deseja armazenar (geralmente uma pasta de projetos) e abra seu editor de código na pasta.

```bash
mkdir projeto-typescript
cd projeto-typescript
```

## Configuração inicial do NPM

```bash
npm init -y
```

O `-y` faz com que a execução inicie e finalize rapidamente, sem preencher o questionário.

## Instalando as dependências de desenvolvimento

```bash
npm install typescript @types/node ts-node --save-dev
```

## Configurando o `tsconfig.json`

Há duas formas, você pode executar o comando `npx tsc --init` (com os parâmetros necessários) ou apenas utilizar o JSON abaixo, vou fornecer as duas opções:

```bash
npx tsc --init --rootDir src --outDir build \
--esModuleInterop --resolveJsonModule --lib es6 \
--module commonjs --allowJs true --noImplicitAny true
```

```json
{
  "compilerOptions": {
    "target": "es5",                          
    "module": "commonjs",                    
    "lib": ["es6"],                     
    "allowJs": true,
    "outDir": "build",                          
    "rootDir": "src",
    "strict": true,         
    "noImplicitAny": true,
    "esModuleInterop": true,
    "resolveJsonModule": true
  }
}
```

## Criação da pasta `src`

Como definimos no `tsconfig.json` que nosso código estará na pasta `src` devemos criá-la para evitar erros de execução.

```bash
mkdir src
```

Crie um arquivo chamado `index.ts` na pasta e então insira o conteúdo:

```ts
console.log('Hello world!')
```

## Configurando execução usando `npm start`

Acesse seu `package.json` e dentro de `scripts` adicione as seguintes linhas:

```json
"start": "npm run build && node build",
"dev": "npx ts-node ./src",
"build": "tsc"
```

- `start`: irá fazer build e executar seu código, utilize para produção;
- `build`: irá fazer o build do seu projeto;
- `dev`: executará o typescript sem build, utilize para desenvolvimento e testes.

## Como usar os comandos do `package.json`?

Você deve abrir o terminal na raiz do projeto e então executar os comandos dessa forma:

Para start:
```bash
npm start
```
Para dev:
```bash
npm run dev
```
Para build:
```bash
npm run build
```


Esses são somente os passos para começar seu projeto, fique à vontade para explorar outras bibliotecas!
