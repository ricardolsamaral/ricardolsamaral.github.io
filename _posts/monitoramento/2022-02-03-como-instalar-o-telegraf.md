---
title: Como instalar o Telegraf no Ubuntu
author:
  name: Ricardo Amaral
  link: https://github.com/ricardolsamaral
date: 2022-02-04 08:00:00 +0800
categories: [Monitoramento, Telegraf]
tags: [monitoramento, telegraf]
---

Esse é post relacionado ao processo de instalação do Telegraf no ubuntu.

## O que é o Telegraf

O Telegraf é tipo um agente gratuito que permite coletar métricas, e expor essas métricas através de plugins ou até mesmo enviar essas métricas para os principais CMDBs como o Prometheus e o InfluxDB.

Também possui plugins de entrada e saída que pode ser conferido na lista abaixo:

*Telegraf plugins*
* [https://docs.influxdata.com/telegraf/latest/plugins](https://docs.influxdata.com/telegraf/latest/plugins) 


## Instalando o Telegraf no Ubuntu

Faça a importação da chave GPG do repositório para o servidor onde será executado o serviço do telegraf.

```bash
sudo apt install -y gnupg2 curl wget
wget -qO- https://repos.influxdata.com/influxdb.key | sudo apt-key add -
```

Adicione o repositório utilizando o comando abaixo.

```bash
echo "deb https://repos.influxdata.com/debian buster stable" | sudo tee /etc/apt/sources.list.d/influxdb.list
```

Assim que o repositório for adicionado, complete a instalação do Telegraf fazendo o update e rodando o comando install.

```bash
sudo apt update
sudo apt -y install telegraf
```

## Inicie e habilite o serviço de telegraf.
```bash
sudo systemctl daemon-reload
sudo systemctl enable --now telegraf
sudo systemctl start telegraf 
```

Para checar se o serviço está ok, você pode utilizar o seguinte comando
```bash
sudo systemctl status telegraf 
```

## Configurando o serviço do telegraf

Você pode alterar as configurações de coleta e plugin de entrada e saída no arquivo de configuração do telegraf em `/etc/telegraf/telegraf.conf`.

Após qualquer alteração lembre de fazer o restart

```bash
sudo systemctl restart telegraf 
```

## Outros documentos

Para completar a configuração você também consultar a documentação do telegraf nos links abaixo: 

* [Configurando o Telegraf](https://docs.influxdata.com/telegraf/latest/administration/configuration) 
* [Troubleshoot do Telegraf](https://docs.influxdata.com/telegraf/latest/administration/troubleshooting) 