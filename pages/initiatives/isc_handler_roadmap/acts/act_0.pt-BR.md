---

layout: col-sidebar
title: "Ato 0 - Instalando o Linux"
author: "Raphael Moreira"
contributors: 
permalink: /initiatives/isc_handler_roadmap/acts
tags: ["cybersecurity", "linux", "kali", "environment"]

---

{% include writers.html %}

# Ato 0 - Instalando o Linux
Visando objetividade e segurança no processo de aprendizagem, as etapas à seguir irão orientá-lo na criação de um 
[🔍ambiente virtualizado Linux](https://www.redhat.com/pt-br/topics/virtualization/what-is-virtualization), que rodará em cima 
do sistema operacional Windows. A título de referência, estaremos usando um **Windows 10 Professional 22H**.

>**Aviso Legal:** o OWASP não endossa nenhum Vendedor ou Ferramenta ao mencioná-lo abaixo. Se ele é mencionado, é porque
> acreditamos que esteja disponível gratuitamente para uso em projetos de código aberto, e o intuito aqui é ensinar. Sinta-se
> à vontade para usar a ferramenta que mais se adequa a sua necessidade.

## Virtualizando com o VMBox
Você pode obter a cópia mais recente da ferramenta no site do fabricante. Após seguir os procedimentos de instalação, é
vital que você se certifique de que seu Windows possui o recurso Hyper-V ativado. Para isso, execute a seguinte linha de
comando, como **Administrador**, no [🔍PowerShell](https://learn.microsoft.com/pt-br/powershell/scripting/overview?view=powershell-7.4):

```bash
systeminfo
```
Dentre os resultados, você deve encontrar o **Requisitos do Hyper-V: detectado**. Caso não encontre essa opção, não será
possível continuar, pois seu computador não possui a tecnologia necessária.

Se o Hyper-V tiver sido detectado, execute a seguine linha de comando para verificar seu estado:

```bash
get-service | findstr vmcompute
```
Se receber o estado `Stopped`, será necessário reiniciar o computador, no modo BIOS, e ativá-lo.

