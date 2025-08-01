# 🧪 Docker + SonarCloud CI Demo

Este repositório demonstra como configurar um pipeline de integração contínua (CI) no GitHub Actions com **SonarCloud** para análise de código. Ideal para projetos que buscam adotar práticas de qualidade de código desde o início.

---

## 📦 Tecnologias Utilizadas

- Docker (conceitos básicos)
- GitHub Actions
- SonarCloud
- YAML para CI/CD
- Repositório público para testes

---

## 🚀 Objetivo

Aprender como integrar o **SonarCloud** a um projeto versionado no GitHub com um fluxo de CI automatizado usando GitHub Actions. O foco principal é:

- Ativar análise estática automática de código
- Entender como funciona o `sonarcloud-github-action`
- Testar conceitos de DevOps em pequenos projetos

---

## ⚙️ CI/CD Pipeline (`.github/workflows/build.yml`)

```yaml
name: Build
on:
  push:
    branches:
      - main
  pull_request:
    types: [opened, synchronize, reopened]
jobs:
  sonarcloud:
    name: SonarCloud
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
        with:
          fetch-depth: 0
      - name: SonarCloud Scan
        uses: SonarSource/sonarcloud-github-action@master
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
````

---

## 🧪 Como testar

1. Crie um projeto no [SonarCloud](https://sonarcloud.io).
2. Gere um token em **My Account > Security > Generate Tokens**.
3. Adicione o token ao repositório no GitHub:

   * Vá em **Settings > Secrets and variables > Actions**
   * Crie o segredo `SONAR_TOKEN`
4. Faça um `push` na branch `main` ou abra um `pull request`.
5. Verifique a aba **Actions** no GitHub para ver o pipeline rodando.

---

## 📊 Resultado esperado

Após a execução do pipeline, o projeto será analisado automaticamente no painel do [SonarCloud](https://sonarcloud.io) com métricas como:

* Cobertura de testes
* Bugs
* Vulnerabilidades
* Code smells
* Duplicações

---

## 🧠 Aprendizados

* Como configurar o SonarCloud para projetos abertos
* Como usar GitHub Actions para CI simples
* Como aplicar práticas iniciais de DevOps
