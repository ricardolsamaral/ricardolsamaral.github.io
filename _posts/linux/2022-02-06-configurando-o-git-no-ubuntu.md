---
title: Configurando o Git no Ubuntu
author:
  name: Ricardo Amaral
  link: https://github.com/ricardolsamaral
date: 2022-02-06 15:00:00 -0300
categories: [Linux, Ubuntu, DevOps]
tags: [ubuntu, linux, setup, git]
---

> Nesse artigo gostaria de compartilhar um exemplo de setup do Git no Ubuntu.

## Instalando o Git no seu Ubuntu desktop

Caso não tenha instalado o git você pode instalar a partir do seu terminal.

Primeiro faço um update:
```bash
❯ sudo apt update
```

Após isso instale usando o comando:
```bash
❯ sudo apt -y install git
```

Para verificar a versão instalada: 
```bash
❯ git --version
```

## Como Definir um nome de usuário no seu Git

Abra o terminal e digite:
```bash
❯ git config --global user.name "Peter Pan"
```

Para verificar o nome do usuário use o comando:

```bash
❯ git config --global user.name
Peter Pan
```

# Como definir um endereço de email no seu Git

Para definir um email use o comando:
```bash
❯ git config --global user.email "email@exemplo.com.br"
```

Para verificar o email use o comando:
```bash
❯ git config --global user.email
email@exemplo.com.br
```

Se quiser verificar todas as configurações do git:
```bash
❯ git config --list
```