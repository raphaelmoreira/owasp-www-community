---

layout: col-sidebar
title: "Ato I - Observando por trás da cortina"
author: "Raphael Moreira"
contributors: 
permalink: /initiatives/isc_handler_roadmap/acts
tags: ["cybersecurity", "http", "network", "response header", "xss", ""]

---

{% include writers.html %}

[🇺🇸](act_1.md) | 🇧🇷
# Ato I - Observando por trás da cortina
Toda vez que um site é acessado, muita coisa ocorre por baixo dos panos, sob o protocolo [🔍Http](https://pt.wikipedia.org/wiki/Hypertext_Transfer_Protocol).
Isso é facilmente observado através das ferramentas de desenvolvedor do seu navegador, onde é possível acompanhar todo o 
tráfego envolvido em determinado site, bem como outras características, como [🔍Código de Estado (Status Code)](https://www.rfc-editor.org/rfc/rfc9110.html#name-status-codes),
[🔍entre outros](https://developer.chrome.com/docs/devtools/network?hl=pt-br).

Cada requisição exibida na lista refere-se a uma chamada única, podendo um site ter dezenas de requisições que compõe seu 
conteúdo, bem como execuções regulares proveniente de [🔍chamadas assíncronas](https://pt.wikipedia.org/wiki/Comunica%C3%A7%C3%A3o_ass%C3%ADncrona).

Dentre várias informações fornecidas, vamos destacar aqui o **Cabeçalho de Resposta**.

>**Aviso Legal:** o OWASP não endossa nenhum Vendedor ou Ferramenta ao mencioná-lo. Se ele é citado, é porque acreditamos
> que esteja disponível gratuitamente para uso em projetos de código aberto. Sinta-se livre para usar a ferramenta que
> mais se adequa a sua necessidade.

## Cabeçalho de Resposta
Um conjunto de informações adicionais passadas entre cliente e servidor. Ainda que seja personalizável, há um [🔍padrão bem definido](https://developer.mozilla.org/pt-BR/docs/Web/HTTP/Headers)
sobre sua estrutura, conteúdo e uso. Por conta dessa flexibilidade é que invasores tentam manipular esses cabeçalhos a seu favor.

Para observá-los, usaremos o [🔍Google Chrome DevTools](https://developer.chrome.com/docs/devtools/open?hl=pt-br). Pela aba [🔍Rede (Network)](https://developer.chrome.com/docs/devtools/network?hl=pt-br), mantenha o **DevTools** aberto, com foco na aba **Rede (Network)**, e acesse o site `https://google.com`. O primeiro item
da lista será o site que você digitou. Ao clicar sobre ele, você terá acesso a primeira aba, chamada **Cabeçalho (Header)**. 
Nessa lista fornecida, localize a seção **Cabeçalho de Resposta (Response Header)**.

Cada site tem seu próprio conjunto de **Cabeçalho de Resposta**, podendo variar de acordo com a configuração do servidor,
aplicação ou serviço. Não há uma lista correta do que deve ter, pois isso depende de cada site, mas sabemos o que não
deve ter, no que tange cibersegurança.

Em sua lista de boas práticas, o OWASP reúne uma série de recomendações, como [conteúdo sugerido](https://owasp.org/www-project-secure-headers/index.html) e [o que evitar](https://owasp.org/www-project-secure-headers/index.html#prevent-information-disclosure-via-http-headers)
no **Cabeçalho de Resposta**.

## Resumo
Aprendemos, nesse primeito ato, a importância de não só conhecer como as conexões entre computadores ocorrem (Ip), como exploramos 
a importância das Portas. Também vimos que configurações equivocadas podem tornar público serviços que deveriam estar
acessíveis e como a preocupação é importante, afinal, se a porta está disponível, alguém pode bater... ou chutar até ela cair.

---

| [⬆️Retornar ao índice](../index.pt-BR.md) | [Próximo ato➡️](act_2.pt-BR.md) |
|-------------------------------------------|---------------------------------|
