---

layout: col-sidebar
title: "Ato I - Observando por trás da cortina"
author: "Raphael Moreira"
contributors: 
permalink: /initiatives/isc_handler_roadmap/acts
tags: ["cybersecurity", "protocol", http", "network", "response header", "xss"]

---

{% include writers.html %}

[🇺🇸](act_1.md) | 🇧🇷
# Ato I - Observando por trás da cortina
Sempre que um site é acessado, uma série de processos ocorre nos bastidores, seguindo o protocolo [🔍Http](https://pt.wikipedia.org/wiki/Hypertext_Transfer_Protocol). Essa dinâmica 
é facilmente visível por meio das ferramentas de desenvolvedor do seu navegador, onde é possível monitorar todo o tráfego 
relacionado a um determinado site, incluindo características como [🔍Código de Estado (Status Code)](https://www.rfc-editor.org/rfc/rfc9110.html#name-status-codes), [🔍entre outros](https://developer.chrome.com/docs/devtools/network?hl=pt-br).

Cada entrada na lista de requisições representa uma interação única, sendo possível que um site tenha dezenas delas para 
formação do conteúdo. Dentre as diversas informações fornecidas, vamos dar destaque aqui ao **Cabeçalho de Resposta**.

>**Aviso Legal:** o OWASP não endossa nenhum Vendedor ou Ferramenta ao mencioná-lo. Se ele é citado, é porque acreditamos
> que esteja disponível gratuitamente para uso em projetos de código aberto. Sinta-se livre para usar a ferramenta que
> mais se adequa a sua necessidade.

## Cabeçalho de Resposta
Trata-se de um conjunto de informações adicionais passadas entre cliente e servidor. Ainda que seja personalizável, há um [🔍padrão bem definido](https://developer.mozilla.org/en-US/docs/Glossary/Response_header)
sobre sua estrutura, conteúdo e uso. Por conta dessa flexibilidade, é comum invasores tentarem manipulá-lo, logo, é importante 
que os desenvolvedores se atentem a não confiara fim de  esses cabeçalhos a seu favor.

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

| [⬆️Retornar ao índice](../index.pt-BR.md) | [Ir para o Ato 2➡️](act_2.pt-BR.md) |
|-------------------------------------------|-------------------------------------|
