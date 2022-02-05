---
title: Escrevendo um plugin em bash para o Telegraf
author:
  name: Ricardo Amaral
  link: https://github.com/ricardolsamaral
date: 2022-02-05 08:00:00 -0300
categories: [Monitoramento, Telegraf]
tags: [monitoramento, telegraf, bash]
---

Esse é post relacionado ao processo de criação de um plugin em bash para execução no Telegraf.

## O que é o plugin inputs.exec 

O plugin exec executa todos os comandos em paralelo em cada intervalo e analisa as métricas de sua saída em qualquer um dos formatos de dados de entrada aceitos. Este plugin pode ser usado para pesquisar métricas personalizadas de qualquer fonte.

## Configurando o plugin inputs.exec 

Para qualquer script com saída para o influxdb você deve ter uma saída como no exemplo estático abaixo:

```bash
#!/bin/bash
echo 'nomedoplugin,tag1=,tag2=b valor1=42i,valor2=43i,valor3=44i'
```

Após isso poderá ser inserido dentro do arquivo de configuração do telegraf em `/etc/telegraf/telegraf.conf` ou então criando um novo arquivo `.conf` dentro do diretório `/etc/telegraf/telegraf.d`.

O plugin de entrada `inputs.exec` deve conter os seguintes parâmetros:

```bash
[[inputs.exec]]
  ##  Caminho do script
  commands = ["/tmp/test.sh"]

  ## Tempo limite para que cada comando seja concluído.
  timeout = "5s" 

  ## Formato entrada de dados, exemplo: influxdb
  data_format = "influx"
```

Outras informações e exemplo de formatos de dados podem ser encontrados em [Input Data Formats](https://github.com/influxdata/telegraf/blob/master/docs/DATA_FORMATS_INPUT.md)

## Testando o plugin

Uma opção de teste é rodar o `telegraf --config telegraf.conf --test` após ter feito o setup acima ou com um parâmetro de filtro, nesse caso o `exec`.

```bash
telegraf --config telegraf.conf --input-filter exec --output-filter influxdb
```

## Reinicie o serviço do Telegraf

Após qualquer alteração lembre sempre de fazer o restart para ativar o plugin corretamente.

```bash
sudo systemctl restart telegraf 
```

## Outros documentos

* [Configurando o plugin de entrada exec](https://github.com/influxdata/telegraf/blob/master/plugins/inputs/exec/README.md) 
* [Troubleshoot do Telegraf](https://docs.influxdata.com/telegraf/latest/administration/troubleshooting) 