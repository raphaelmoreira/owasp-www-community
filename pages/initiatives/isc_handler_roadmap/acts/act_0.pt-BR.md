---

layout: col-sidebar
title: "Ato 0 - Preparação"
author: "Raphael Moreira"
contributors: 
permalink: /initiatives/isc_handler_roadmap/acts
tags: ["cybersecurity", "kali", "linux", "environment", "virtualization"]

---

{% include writers.html %}

[🇺🇸](act_0.md) | 🇧🇷
# Ato 0 - Preparação
Visando objetividade e segurança no processo de aprendizagem, as etapas à seguir irão orientá-lo na criação de um 
[🔍ambiente virtualizado Linux](https://www.redhat.com/pt-br/topics/virtualization/what-is-virtualization). A título de referência, estaremos usando um **Microsoft Windows 10 Pro**, versão **22H2**, 
compilação **19045.4123**. 

A distribuição sugerida é a [🔍Kali](https://www.kali.org/).

>**Aviso legal:** o OWASP não endossa nenhum Vendedor ou Ferramenta ao mencioná-lo. Se ele é citado, é porque acreditamos 
> que esteja disponível gratuitamente para uso em projetos de código aberto. Sinta-se livre para usar a ferramenta que 
> mais se adequa à sua necessidade.

## Kali Linux
A [🔍distribuição Kali](https://www.kali.org/features/) é dedicada a cibersegurança, provendo um conjunto de ferramentas propícias para a tarefa. 
Se você tem afinidade com outra distribuição, não é necessário trocá-lo pelo Kali, pois ao longo dos atos, haverá orientação 
sobre cada ferramenta, e como obtê-la.

No site oficial do Kali você encontra diversas [plataformas](https://www.kali.org/get-kali/#kali-platforms), contudo, para nossa iniciativa, usaremos o [VMware](https://cdimage.kali.org/kali-2024.1/kali-linux-2024.1-vmware-amd64.7z).
Caso não se sinta à vontade com essa ferramenta de virtualização, o site disponibiliza [outras opções](https://www.kali.org/get-kali/#kali-virtual-machines).

>**ATENÇÃO:** certifique de que seu sistema operacional possui o 
> [🔍Hyper-V](https://learn.microsoft.com/pt-br/virtualization/hyper-v-on-windows/about/) habilitado, caso contrário,
> terá problemas com a virtualização.

## Recomendações

Assim que seu ambiente estiver funcional, isto é, virtualização configurada e distribuições funcional, lembre-se que tudo 
que vamos mostrar no decorrer dessa iniciativa, requer elevação de privilégios (acesso administrativo). No entanto, é altamente 
recomendável que você não use o usuário **root** para isso. Procure criar outro, marcando-o como **Administrador**. Embora 
pareça a mesma coisa, não é. O usuário **root** possui privilégios que podem te colocar em risco, se usado de maneira incorreta. 

Outro item relevante é ativar a criptograria da imagem virtualizada. Ainda que você esteja em estágios iniciais de
aprendizado, procure internalizar a cultura de proteger também o ambiente em que você irá trabalhar, já que somente assim
você garantirá, desde o início, a privacidade do seu trabalho.
---

| [⬆️Retornar ao índice](../index.pt-BR.md) | [Ir para o Ato 1](act_1.pt-BR.md)➡️ |
|-------------------------------------------|-------------------------------------|

