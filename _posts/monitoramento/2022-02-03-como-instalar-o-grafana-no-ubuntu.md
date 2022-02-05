---
title: Como instalar o Grafana no Ubuntu
author:
  name: Ricardo Amaral
  link: https://github.com/ricardolsamaral
date: 2022-02-03 08:00:00 -0300
categories: [Monitoramento, Grafana]
tags: [monitoramento, grafana]
---

> Esse é post relacionado ao processo de instalação do Grafana no ubuntu.

## O que é o Grafana

O Grafana é uma ferramenta gratuita que permite gerenciar e criar dashboards para visualização de métricas utilizando os principais CMDBs, como o Prometheus e o InfluxDB, assim como outras fontes de dados como MySQL, Graphite, PostgreSQL e Elasticsearch. 

## Instalando o Grafana no Ubuntu

Para instalar a última versão disponível  do Grafana, adicione o seguinte repositório no seu servidor utilizando os comandos abaixo:

```bash
sudo apt-get install -y apt-transport-https
sudo apt-get install -y software-properties-common wget 
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
```

Use este repositório para as versões estáveis

```bash
echo "deb https://packages.grafana.com/oss/deb stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
```

Após isso realize a atualização e a instalação

```bash
sudo apt-get update
sudo apt-get -y install grafana
```

E inicie o serviço do Grafana

```bash
sudo systemctl daemon-reload
sudo systemctl enable --now grafana-server
```

Para checar se o serviço está ok, você pode utilizar o seguinte comando

```bash
sudo systemctl status grafana-server 
```

E caso seja necessário iniciar o servidor faço o start com o systemctl

```bash
sudo systemctl start grafana-server
```

## Como acessar o Grafana

Para acessar o grafana use a url local (por padrão 0.0.0.0:3000 ou 127.0.0.1:3000).
Ou utilize o *netstat* para verificar qual o IP que está escutando na porta 3000.

http://seu-ip:3000

E depois use a senha abaixo para fazer o primeiro login:

```bash
Usuário: admin
Senha: admin
```

> `Lembre de alterar a senha e alterar o usuário de administração.`