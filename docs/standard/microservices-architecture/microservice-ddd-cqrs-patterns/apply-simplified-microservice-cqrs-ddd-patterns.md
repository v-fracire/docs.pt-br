---
title: "Aplicando padrões CQRS e DDD simplificados em um microsserviço."
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Aplicando padrões CQRS e DDD simplificados em um microsserviço."
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 99fd7ce32039742e23f8e01aa4c33cddd7a9f698
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="applying-simplified-cqrs-and-ddd-patterns-in-a-microservice"></a><span data-ttu-id="976b0-104">Aplicando padrões CQRS e DDD simplificados em um microsserviço.</span><span class="sxs-lookup"><span data-stu-id="976b0-104">Applying simplified CQRS and DDD patterns in a microservice</span></span>

<span data-ttu-id="976b0-105">CQRS é um padrão de arquitetura que separa os modelos para ler e gravar dados.</span><span class="sxs-lookup"><span data-stu-id="976b0-105">CQRS is an architectural pattern that separates the models for reading and writing data.</span></span> <span data-ttu-id="976b0-106">O termo relacionado [separação de consulta de comando (CQS)](https://martinfowler.com/bliki/CommandQuerySeparation.html) foi originalmente definido por Bertrand Meyer em seu livro *construção de Software orientada a objeto*.</span><span class="sxs-lookup"><span data-stu-id="976b0-106">The related term [Command Query Separation (CQS)](https://martinfowler.com/bliki/CommandQuerySeparation.html) was originally defined by Bertrand Meyer in his book *Object Oriented Software Construction*.</span></span> <span data-ttu-id="976b0-107">A ideia básica é que você pode dividir operações do sistema em duas categorias nitidamente separadas:</span><span class="sxs-lookup"><span data-stu-id="976b0-107">The basic idea is that you can divide a system’s operations into two sharply separated categories:</span></span>

-   <span data-ttu-id="976b0-108">Consultas.</span><span class="sxs-lookup"><span data-stu-id="976b0-108">Queries.</span></span> <span data-ttu-id="976b0-109">Esses retornam um resultado e não altera o estado do sistema e são livres de efeitos colaterais.</span><span class="sxs-lookup"><span data-stu-id="976b0-109">These return a result and do not change the state of the system, and they are free of side effects.</span></span>

-   <span data-ttu-id="976b0-110">Os comandos.</span><span class="sxs-lookup"><span data-stu-id="976b0-110">Commands.</span></span> <span data-ttu-id="976b0-111">Esses alterar o estado de um sistema.</span><span class="sxs-lookup"><span data-stu-id="976b0-111">These change the state of a system.</span></span>

<span data-ttu-id="976b0-112">CQS é um conceito simple — é sobre métodos de dentro do mesmo objeto sendo consultas ou comandos.</span><span class="sxs-lookup"><span data-stu-id="976b0-112">CQS is a simple concept—it is about methods within the same object being either queries or commands.</span></span> <span data-ttu-id="976b0-113">Cada método retorna o estado ou muda de estado, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="976b0-113">Each method either returns state or mutates state, but not both.</span></span> <span data-ttu-id="976b0-114">Até mesmo um objeto de padrão único repositório pode estar em conformidade com CQS.</span><span class="sxs-lookup"><span data-stu-id="976b0-114">Even a single repository pattern object can comply with CQS.</span></span> <span data-ttu-id="976b0-115">CQS pode ser considerado um princípio fundamental para CQRS.</span><span class="sxs-lookup"><span data-stu-id="976b0-115">CQS can be considered a foundational principle for CQRS.</span></span>

<span data-ttu-id="976b0-116">[Comando e consulta responsabilidade CQRS (segregação)](https://martinfowler.com/bliki/CQRS.html) foi introduzido por Greg Young e altamente promovido pelos Udi Dahan e outros.</span><span class="sxs-lookup"><span data-stu-id="976b0-116">[Command and Query Responsibility Segregation (CQRS)](https://martinfowler.com/bliki/CQRS.html) was introduced by Greg Young and strongly promoted by Udi Dahan and others.</span></span> <span data-ttu-id="976b0-117">Ele se baseia no princípio CQS, embora mais detalhada.</span><span class="sxs-lookup"><span data-stu-id="976b0-117">It is based on the CQS principle, although it is more detailed.</span></span> <span data-ttu-id="976b0-118">Ele pode ser considerado um padrão com base em comandos e eventos mais opcionalmente nas mensagens assíncronas.</span><span class="sxs-lookup"><span data-stu-id="976b0-118">It can be considered a pattern based on commands and events plus optionally on asynchronous messages.</span></span> <span data-ttu-id="976b0-119">Em muitos casos, a CQRS está relacionado a cenários mais avançados, como ter um banco de dados diferente para leituras (consultas) que, para gravações (atualizações).</span><span class="sxs-lookup"><span data-stu-id="976b0-119">In many cases, CQRS is related to more advanced scenarios, like having a different physical database for reads (queries) than for writes (updates).</span></span> <span data-ttu-id="976b0-120">Além disso, um sistema CQRS mais evoluído pode implementar [(ES) de fornecimento do evento](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/) para seu banco de dados de atualizações, assim você deve apenas armazenar eventos no modelo de domínio em vez de armazenar os dados de estado atual.</span><span class="sxs-lookup"><span data-stu-id="976b0-120">Moreover, a more evolved CQRS system might implement [Event-Sourcing (ES)](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/) for your updates database, so you would only store events in the domain model instead of storing the current-state data.</span></span> <span data-ttu-id="976b0-121">No entanto, isso não é a abordagem usada neste guia; Estamos usando a abordagem mais simples de CQRS, que consiste em separar apenas as consultas dos comandos.</span><span class="sxs-lookup"><span data-stu-id="976b0-121">However, this is not the approach used in this guide; we are using the simplest CQRS approach, which consists of just separating the queries from the commands.</span></span>

<span data-ttu-id="976b0-122">O aspecto de separação de CQRS é obtido com o agrupamento de operações de consulta em uma camada e comandos em outra camada.</span><span class="sxs-lookup"><span data-stu-id="976b0-122">The separation aspect of CQRS is achieved by grouping query operations in one layer and commands in another layer.</span></span> <span data-ttu-id="976b0-123">Cada camada tem seu próprio modelo de dados (Observe que dizemos que o modelo, não necessariamente um banco de dados diferente) e é criada usando seu próprio combinação de padrões e tecnologias.</span><span class="sxs-lookup"><span data-stu-id="976b0-123">Each layer has its own data model (note that we say model, not necessarily a different database) and is built using its own combination of patterns and technologies.</span></span> <span data-ttu-id="976b0-124">Além disso, as duas camadas podem ser dentro do mesmo nível ou microsserviço, como no exemplo (ordem microsserviço) usado para este guia.</span><span class="sxs-lookup"><span data-stu-id="976b0-124">More importantly, the two layers can be within the same tier or microservice, as in the example (ordering microservice) used for this guide.</span></span> <span data-ttu-id="976b0-125">Ou eles podem ser implementados em microservices diferente ou processos para que possa ser otimizados e expandidos separadamente sem afetar uma da outra.</span><span class="sxs-lookup"><span data-stu-id="976b0-125">Or they could be implemented on different microservices or processes so they can be optimized and scaled out separately without affecting one another.</span></span>

<span data-ttu-id="976b0-126">CQRS significa ter dois objetos para uma operação de leitura/gravação em que em outros contextos houver.</span><span class="sxs-lookup"><span data-stu-id="976b0-126">CQRS means having two objects for a read/write operation where in other contexts there is one.</span></span> <span data-ttu-id="976b0-127">Há motivos para ter um banco de dados desnormalizados leituras, que você pode aprender sobre na literatura CQRS mais avançada.</span><span class="sxs-lookup"><span data-stu-id="976b0-127">There are reasons to have a denormalized reads database, which you can learn about in more advanced CQRS literature.</span></span> <span data-ttu-id="976b0-128">Mas não estamos usando essa abordagem aqui, onde o objetivo é ter mais flexibilidade em consultas, em vez de limitar as consultas com restrições de padrões DDD como agregações.</span><span class="sxs-lookup"><span data-stu-id="976b0-128">But we are not using that approach here, where the goal is to have more flexibility in the queries instead of limiting the queries with constraints from DDD patterns like aggregates.</span></span>

<span data-ttu-id="976b0-129">Um exemplo desse tipo de serviço é o ordenação microsserviço do aplicativo eShopOnContainers referência.</span><span class="sxs-lookup"><span data-stu-id="976b0-129">An example of this kind of service is the ordering microservice from the eShopOnContainers reference application.</span></span> <span data-ttu-id="976b0-130">Este serviço implementa um microsserviço com base em uma abordagem CQRS simplificada.</span><span class="sxs-lookup"><span data-stu-id="976b0-130">This service implements a microservice based on a simplified CQRS approach.</span></span> <span data-ttu-id="976b0-131">Ele usa uma fonte de dados ou banco de dados, mas dois modelos lógicos mais padrões DDD para o domínio transacional, conforme mostrado na Figura 9-2.</span><span class="sxs-lookup"><span data-stu-id="976b0-131">It uses a single data source or database, but two logical models plus DDD patterns for the transactional domain, as shown in Figure 9-2.</span></span>

![](./media/image2.png)

<span data-ttu-id="976b0-132">**Figura 9-2**.</span><span class="sxs-lookup"><span data-stu-id="976b0-132">**Figure 9-2**.</span></span> <span data-ttu-id="976b0-133">Simplificado CQRS DDD baseada e microsserviço</span><span class="sxs-lookup"><span data-stu-id="976b0-133">Simplified CQRS- and DDD-based microservice</span></span>

<span data-ttu-id="976b0-134">A camada de aplicativo pode ser a própria API da Web.</span><span class="sxs-lookup"><span data-stu-id="976b0-134">The application layer can be the Web API itself.</span></span> <span data-ttu-id="976b0-135">O aspecto de design importante aqui é que o microsserviço dividiu as consultas e ViewModels (modelos de dados criados especialmente para os aplicativos cliente) do modelo de domínio, comandos e transações após o padrão CQRS.</span><span class="sxs-lookup"><span data-stu-id="976b0-135">The important design aspect here is that the microservice has split the queries and ViewModels (data models especially created for the client applications) from the commands, domain model, and transactions following the CQRS pattern.</span></span> <span data-ttu-id="976b0-136">Essa abordagem mantém as consultas independentes de restrições e restrições provenientes de padrões DDD que só fazem sentido para transações e atualizações, conforme explicado nas seções posteriores.</span><span class="sxs-lookup"><span data-stu-id="976b0-136">This approach keeps the queries independent from restrictions and constraints coming from DDD patterns that only make sense for transactions and updates, as explained in later sections.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="976b0-137">[Anterior] (index.md) [Avançar] (eshoponcontainers-cqrs-ddd-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="976b0-137">[Previous] (index.md) [Next] (eshoponcontainers-cqrs-ddd-microservice.md)</span></span>