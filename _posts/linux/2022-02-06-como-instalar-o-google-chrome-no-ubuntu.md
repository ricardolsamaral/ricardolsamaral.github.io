---
title: Como instalar o Google Chrome no Ubuntu
author:
  name: Ricardo Amaral
  link: https://github.com/ricardolsamaral
date: 2022-02-06 18:00:00 -0300
categories: [Linux, Ubuntu]
tags: [ubuntu, linux, setup, git, devops]
---

> Esse é post relacionado ao processo de instalação do Google Chrome no Ubuntu.

## Atualize e instale o wget

Primeiro faço um update:
```bash
❯ sudo apt update
```

Caso não esteja instalado o wget, faça isso usando o comando abaixo:

```bash
❯ sudo apt -y install wget
```

Para verificar a versão instalada: 
```bash
❯ wget --version
```

## Instalando o Google Chrome via wget

Para instalar a versão estável mais recente do pacote google-chrome-stable utilize os comando abaixo.

Primeiro baixo o .deb utilizando o comando wget:
```bash
❯ wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```

Após isso instale o pacote google-chrome-stable_current_amd64.deb utilizando o comando do dpkg: 
```bash
❯ sudo dpkg -i google-chrome-stable_current_amd64.deb 
```
## Instale as dependências

Para instalar as dependências dos pacotes:
```bash
❯ sudo apt-get install -f 
```