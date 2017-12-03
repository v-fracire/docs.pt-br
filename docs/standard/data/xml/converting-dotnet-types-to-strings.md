---
title: Convertendo tipos do .NET Framework para cadeias de caracteres
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c3abe140e62f112a15a1ad1b1b2a79c14364b26d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="converting-net-framework-types-to-strings"></a><span data-ttu-id="9551e-102">Convertendo tipos do .NET Framework para cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="9551e-102">Converting .NET Framework Types to Strings</span></span>
<span data-ttu-id="9551e-103">Se você quiser converter um tipo .NET Framework em uma cadeia de caracteres, use o **ToString** método.</span><span class="sxs-lookup"><span data-stu-id="9551e-103">If you want to convert a .NET Framework type to a string, use the **ToString** method.</span></span> <span data-ttu-id="9551e-104">O **ToString** método retorna uma representação de cadeia de caracteres do tipo transmitido.</span><span class="sxs-lookup"><span data-stu-id="9551e-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="9551e-105">A tabela a seguir lista os tipos do.NET Framework que retorna uma cadeia de caracteres em um formato que mapeia a (XSD) de esquema XML as especificações.</span><span class="sxs-lookup"><span data-stu-id="9551e-105">The following table lists the .NET Framework types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="9551e-106">Tipo do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9551e-106">.NET Framework type</span></span>|<span data-ttu-id="9551e-107">Tipo cadeia de caracteres retornado</span><span class="sxs-lookup"><span data-stu-id="9551e-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="9551e-108">Boolean</span><span class="sxs-lookup"><span data-stu-id="9551e-108">Boolean</span></span>|<span data-ttu-id="9551e-109">"true", "false"</span><span class="sxs-lookup"><span data-stu-id="9551e-109">"true", "false"</span></span>|  
|<span data-ttu-id="9551e-110">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="9551e-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="9551e-111">"INF"</span><span class="sxs-lookup"><span data-stu-id="9551e-111">"INF"</span></span>|  
|<span data-ttu-id="9551e-112">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="9551e-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="9551e-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="9551e-113">"-INF"</span></span>|  
|<span data-ttu-id="9551e-114">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="9551e-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="9551e-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="9551e-115">"INF"</span></span>|  
|<span data-ttu-id="9551e-116">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="9551e-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="9551e-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="9551e-117">"-INF"</span></span>|  
|<span data-ttu-id="9551e-118">DateTime</span><span class="sxs-lookup"><span data-stu-id="9551e-118">DateTime</span></span>|<span data-ttu-id="9551e-119">O formato é yyyy-MM-ddTHH:mm:sszzzzzz e seus subconjuntos.</span><span class="sxs-lookup"><span data-stu-id="9551e-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="9551e-120">Timespan</span><span class="sxs-lookup"><span data-stu-id="9551e-120">Timespan</span></span>|<span data-ttu-id="9551e-121">O formato é PnYnMnTnHnMnS, por exemplo, `P2Y10M15DT10H30M20S` é uma duração de 2 anos, meses 10, 15 dias, 10hours, 30 minutos e 20 segundos.</span><span class="sxs-lookup"><span data-stu-id="9551e-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9551e-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9551e-122">See Also</span></span>  
 [<span data-ttu-id="9551e-123">Conversão de tipos de dados XML</span><span class="sxs-lookup"><span data-stu-id="9551e-123">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [<span data-ttu-id="9551e-124">Convertendo cadeias de caracteres para tipos de dados do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9551e-124">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)