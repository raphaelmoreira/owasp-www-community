---

layout: col-sidebar
title: "Ato I - Portas, portas e mais portas"
author: "Raphael Moreira"
contributors: 
permalink: /initiatives/isc_handler_roadmap/acts
tags: ["cybersecurity", "port", "tcp", "udp", "scan"]

---

{% include writers.html %}

# Ato I - Porta para todos os lugares
Toda a internet funciona em cima de um [Protocolo de Internet (IP)](https://en.wikipedia.org/wiki/IP_address), que nada 
mais é que um endereço único daquilo que você procura. Como uma lista telefônica, onde pesquisamos nomes de estabelecimentos 
ao invés de ruas, com a internet é igual: é mais fácil lembrarmos de nomes do que uma sequência numérica. E esses nomes, 
chamamos de [Domain Name System (DNS)](https://en.wikipedia.org/wiki/Domain_Name_System).

## Aprofundando
Quando você acessa um site qualquer, como o https://google.com.br, na verdade, seu computador está acessando um IP (ex: `142.251.129.99`). 
O que ocorre é que no meio do caminho, o DNS entra em cena e busca esse nome em um catálogo, e localiza o IP equivalente. 
Você pode visualizar isso agora mesmo, em seu computador:

**Windows - [prompt de comando](https://pt.wikipedia.org/wiki/Cmd.exe)**
```bash
tracert google.com.br
```

**Linux - [terminal/shell](https://pt.wikipedia.org/wiki/Shell_do_Unix)**
```bash
traceroute google.com.br
```
Dependendo do site que você analisar, o IP retornado pode ter padrões diferentes. Se visualizar quatro grupos (ex: `0.0.0.0`), 
indica que é o [Ipv4](https://pt.wikipedia.org/wiki/IPv4). No caso de oito grupos (ex: `0000:0000:0000:0000:0000:0000:0000:0000`), 
significa que é um [Ipv6](https://pt.wikipedia.org/wiki/IPv6). Independende de qual seja, sua serventia é a mesma: conectar o 
ponto A ao ponto B.

A sua própria máquina, inclusive, possui um IP, e você pode conferir isso da seguinte forma:

**Windows - prompt de comando**
```bash
ipconfig
```

**Linux - terminal/shell**
```bash
ipconfig
```
Contudo, se você digitar o IP obtido em seu navegador, ele não vai te levar para lugar nenhum. Isso porque o IP que está 
vendo é algo local, chamado de [Intranet](https://pt.wikipedia.org/wiki/Intranet), isto é, visível apenas para você.

Caso queira ver "quem é você" de verdade na internet, é necessário uma ferramenta que lhe diga isso, como por exemplo, o https://ipconfig.me/.
Note que o número IP obtido é bem diferente do que você recebeu em sua intranet. O IP que está vendo é o seu, ou melhor, o 
seu e de todo um grupo de dispositivos que fazem uso do mesmo provedor de internet.

Agora que você compreende o IP, internet e intranet, vamos falar de portas e como elas são importantes.

## A garota que mora ao lado

