---
title: "Usando comandos do Windows PowerShell em um DockerFile para configurar a contêineres do Windows (Docker padrão com base)"
description: "Ciclo de vida de aplicativo de Docker em contêineres com ferramentas e plataformas da Microsoft"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.openlocfilehash: f7e92b0f1c749e2c00e3afc4ffcfc2fc88d7628f
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2017
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="958c1-104">Usando comandos do Windows PowerShell em um DockerFile para configurar a contêineres do Windows (Docker padrão com base)</span><span class="sxs-lookup"><span data-stu-id="958c1-104">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="958c1-105">Com [contêineres do Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), você pode converter seus aplicativos existentes do Windows para imagens do Docker e implantá-los com as mesmas ferramentas que o resto do ecossistema do Docker.</span><span class="sxs-lookup"><span data-stu-id="958c1-105">With [Windows Containers](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="958c1-106">Para usar contêineres do Windows, você apenas precisa gravar comandos do Windows PowerShell no DockerFile, conforme demonstrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="958c1-106">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="958c1-107">Nesse caso, estamos usando o Windows PowerShell para instalar uma imagem base do Windows Server Core, bem como o IIS.</span><span class="sxs-lookup"><span data-stu-id="958c1-107">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="958c1-108">De maneira semelhante, você também pode usar comandos do Windows PowerShell para configurar componentes adicionais como o tradicional ASP.NET 4. x e o .NET 4.6 ou qualquer outro software do Windows, como mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="958c1-108">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
<span data-ttu-id="958c1-109">[Anterior] (visual-studio-ferramentas-para-docker.md) [Avançar] (... /docker-DevOps-Workflow/index.MD)</span><span class="sxs-lookup"><span data-stu-id="958c1-109">[Previous] (visual-studio-tools-for-docker.md) [Next] (../docker-devops-workflow/index.md)</span></span>