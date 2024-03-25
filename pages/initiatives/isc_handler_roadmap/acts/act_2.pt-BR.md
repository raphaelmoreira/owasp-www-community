---

layout: col-sidebar
title: "Ato II - Portas, portas e mais portas"
author: "Raphael Moreira"
contributors: 
permalink: /initiatives/isc_handler_roadmap/acts
tags: ["cybersecurity", "port", "tcp", "udp", "scan", "nmap"]

---

{% include writers.html %}

[🇺🇸](act_2.md) | 🇧🇷
# Ato II - Porta para todos os lugares
Toda a internet funciona em cima de um [🔍Protocolo de Internet (IP)](https://pt.wikipedia.org/wiki/Endere%C3%A7o_IP) e 
sua respectiva [🔍Porta](https://pt.wikipedia.org/wiki/Porta_(redes_de_computadores)), que nada mais faz que gerar um endereço 
único do serviço que você procura. Como uma lista telefônica, onde pesquisamos os nomes dos estabelecimentos para encontrar 
a rua e o número, com a internet é igual: é mais fácil lembrarmos de nomes ao invés de uma sequência numérica. E a esses 
nomes, chamamos de [🔍Sistema de Nomes de Domínio (DNS)](https://pt.wikipedia.org/wiki/Sistema_de_Nomes_de_Dom%C3%ADnio).

## O que você irá aprender ao final desse ato:
- O que é IP, como descobrir o seu e dos sites que visitou;
- O que são Portas e qual sua relação com o IP;
- Como Ip e Porta, juntos, estabelecem conexões simultâneas;
- Como explorar serviços expostos na internet;
- Os riscos de um serviço mal configurado;

## Protocolo de Internet
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

## A garota que mora na porta ao lado
No seu computador, quando um software se conecta à internet (sites, streaming ou jogos), ele o faz através do IP. Contudo,
para que não haja conflito, cada número IP é acompanhado de uma [Porta](https://pt.wikipedia.org/wiki/Porta_(redes_de_computadores)), 
na estrutura `IP:Porta`, conforme exemplificado abaixo:
```
192.168.0.1:666
```
Você pode averiguar isso neste momento, através do comando:

**Windows - prompt de comando**
```bash
netstat -na
```

**Linux - terminal/shell**
```bash
netstat -na
```
Perceba que, dentre a lista de resultados, você encontrará seu ip interno (intranet) diversas vezes, só que apontando 
para algum outro IP relacionado à um serviço público na internet. Note que para cada conexão estabelecida, há uma porta única:

```
TCP    192.168.0.66:49508     52.226.139.180:443     ESTABLISHED
TCP    192.168.0.66:51790     52.226.139.180:443     ESTABLISHED
TCP    192.168.0.66:53231     162.125.5.18:443       ESTABLISHED
TCP    192.168.0.66:53723     20.44.10.122:443       ESTABLISHED
```
Quando você lê notícias sobre crackers que usam máquinas zumbis, para coordenar ataques massivos contra um alvo específico, 
saiba que essa é uma forma de fazer: ao alojar um Worm na máquia hospedeiro, este pode abrir uma porta clandestina em seu
computador, aguardando a ordem para fazer disparos contra o alvo. É um exemplo simples, claro, mas de fácil compreensão sobre
como essas coisas acontecem.

## O que a porta diz sobre seu serviço
Até aqui pudemos ver, de forma simplificada, como as portas são relevantes para cada a conexão entre dispositivos. Ao todo,
temos 65.535 portas, embora nem todas sejam de uso comum. As mais conhecidas, usados na indústria, giram em torno de 100. 
Cada serviço e/ou produto pode se firmar numa delas, como por exemplo, o Microsoft Sql Server (1433), Ftp (21), Http (80), 
entre outras.

Saber o número dessas portas não é, de fato, uma falha de segurança. Mas compreender o que cada um representa é, pois determinados
acessos não deveriam estar acessíveis publicamente, principalmente quando são de uso interno, como um Banco de Dados. Essas falhas
de design podem ocorrem por diversos fatores, como falta de conhecimento ou configuração inadequada, ou seja: falha humana.

Costumamos sempre achar que nada vai ocorrer conosco ou que nosso produto é pequeno demais para ser visado. Mas isso é um erro
primordial, pois o atacante sempre vai por essa via, na confiança de que você pensa dessa forma, e por isso, não se preocupou com
a configuração do seu serviço.

## Explorando
Para explorar como esse tipo de evento ocorre, precisamos de ferramentário apropriado, portanto, a partir daqui, iremos nos
focar apenas num único sistema operacional, que será o Linux. Precisamente, através da distribuição Kali.

> ATENÇÃO: todas as etapas à seguir são de cunho educativo e não foram executadas em ambiente reais. Efetuar os processos a
> seguir, sem o conscentimento do alvo, é crime cibernético. Seja ético, pois estamos aqui para nos defender e não comprometer.

Uma ferramenta boa para nos dar apoio nesta demanda, é o Nmap. Essa sondagem é feita usando-se o protocolo básico de "aperto de mãos",
entre origem e destino. O Nmap enviar uma solicitação (SYN) e espera uma resposta (ACK). Caso afirmativo, isso é o indicativo
de que aquele destino está aberto e aguardando conexões. Logo, podemos obter detalhes significativos sobre quais serviços são
esses:

```bash
nmap dominio.com

--resultados
```
Os resultados que podemos obter podem variar de alvo para alvo, logo, o intuito aqui é saber quais são. Alguns, são esperados, 
como é o caso da 53 (domain), 443 (https), outras, podemos questionar se precisam realmente estar disponíveis 24/7, como 22 (SSH),
43 (SMTP) enquanto de algumas definitivamente não deveria estar ali, como 1433 (sql server), 80 (http) ou 23 (Telnet).

É sempre bom conferir a tabela de portas, para assegurar se ela deveria realmente estar disponível para qualquer um. E se estiver,
providencie a remoção.

> **ATENÇÃO**: cada execução equivale a uma requisição, logo, execuções subsequentes ou initerruptas podem causar falhas, lentidão ou
> mesmo bloqueio do serviço, pois defesas como WAF podem agir. Não faça isso de forma clandestina.

## Resumo
Aprendemos, nesse primeito ato, a importância de não só conhecer como as conexões entre computadores ocorrem (Ip), como exploramos 
a importância das Portas. Também vimos que configurações equivocadas podem tornar público serviços que deveriam estar
acessíveis e como a preocupação é importante, afinal, se a porta está disponível, alguém pode bater... ou chutar até ela cair.

---

| [⬆️Retornar ao índice](../index.pt-BR.md) | [⬅️Ato anterior](act_1.pt-BR.md) | Próximo ato (em breve)➡️ |
|-------------------------------------------|----------------------------------|--------------------------|

