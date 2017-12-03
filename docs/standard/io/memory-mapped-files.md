---
title: "Arquivos mapeados na memória"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- memory-mapped files
- inter-process communiation
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
caps.latest.revision: "24"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2602d431aada7b3e0ee226eed319903492022ae9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="memory-mapped-files"></a><span data-ttu-id="a040f-102">Arquivos mapeados na memória</span><span class="sxs-lookup"><span data-stu-id="a040f-102">Memory-Mapped Files</span></span>
<span data-ttu-id="a040f-103">Um arquivo mapeado pela memória tem o conteúdo de um arquivo em memória virtual.</span><span class="sxs-lookup"><span data-stu-id="a040f-103">A memory-mapped file contains the contents of a file in virtual memory.</span></span> <span data-ttu-id="a040f-104">Esse mapeamento entre um espaço de arquivo e memória permite que um aplicativo, incluindo vários processos, modifique o arquivo, ler e gravar diretamente para a memória.</span><span class="sxs-lookup"><span data-stu-id="a040f-104">This mapping between a file and memory space enables an application, including multiple processes, to modify the file by reading and writing directly to the memory.</span></span> <span data-ttu-id="a040f-105">Começando com o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], você pode usar código gerenciado para acessar arquivos mapeados na memória da mesma maneira que funções nativas do Windows acessar arquivos mapeados na memória, conforme descrito em [Managing Memory-Mapped arquivos Win32](http://go.microsoft.com/fwlink/?linkid=180801).</span><span class="sxs-lookup"><span data-stu-id="a040f-105">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use managed code to access memory-mapped files in the same way that native Windows functions access memory-mapped files, as described in [Managing Memory-Mapped Files in Win32](http://go.microsoft.com/fwlink/?linkid=180801).</span></span>  
  
 <span data-ttu-id="a040f-106">Há dois tipos de arquivos mapeados na memória:</span><span class="sxs-lookup"><span data-stu-id="a040f-106">There are two types of memory-mapped files:</span></span>  
  
-   <span data-ttu-id="a040f-107">Arquivos de memória mapeada persistentes</span><span class="sxs-lookup"><span data-stu-id="a040f-107">Persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="a040f-108">Arquivos persistentes são arquivos mapeados na memória que estão associados um arquivo de origem em um disco.</span><span class="sxs-lookup"><span data-stu-id="a040f-108">Persisted files are memory-mapped files that are associated with a source file on a disk.</span></span> <span data-ttu-id="a040f-109">Quando a última terminar o processo de trabalho com o arquivo, os dados são salvos no arquivo de origem no disco.</span><span class="sxs-lookup"><span data-stu-id="a040f-109">When the last process has finished working with the file, the data is saved to the source file on the disk.</span></span> <span data-ttu-id="a040f-110">Esses arquivos mapeados na memória são adequados para trabalhar com arquivos de origem muito grande.</span><span class="sxs-lookup"><span data-stu-id="a040f-110">These memory-mapped files are suitable for working with extremely large source files.</span></span>  
  
-   <span data-ttu-id="a040f-111">Não persistente arquivos mapeados na memória</span><span class="sxs-lookup"><span data-stu-id="a040f-111">Non-persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="a040f-112">Arquivos não persistente são arquivos mapeados na memória que não estão associados um arquivo em um disco.</span><span class="sxs-lookup"><span data-stu-id="a040f-112">Non-persisted files are memory-mapped files that are not associated with a file on a disk.</span></span> <span data-ttu-id="a040f-113">Quando a última terminar o processo de trabalho com o arquivo, os dados serão perdidos e o arquivo é recuperado pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a040f-113">When the last process has finished working with the file, the data is lost and the file is reclaimed by garbage collection.</span></span> <span data-ttu-id="a040f-114">Esses arquivos são adequados para a criação de memória compartilhada para comunicação entre processos (IPC).</span><span class="sxs-lookup"><span data-stu-id="a040f-114">These files are suitable for creating shared memory for inter-process communications (IPC).</span></span>  
  
## <a name="processes-views-and-managing-memory"></a><span data-ttu-id="a040f-115">Processos, modos de exibição e gerenciamento de memória</span><span class="sxs-lookup"><span data-stu-id="a040f-115">Processes, Views, and Managing Memory</span></span>  
 <span data-ttu-id="a040f-116">Arquivos mapeados na memória podem ser compartilhados entre vários processos.</span><span class="sxs-lookup"><span data-stu-id="a040f-116">Memory-mapped files can be shared across multiple processes.</span></span> <span data-ttu-id="a040f-117">Processos podem mapear para o mesmo arquivo de mapeamento de memória usando um nome comum, que é atribuído pelo processo que criou o arquivo.</span><span class="sxs-lookup"><span data-stu-id="a040f-117">Processes can map to the same memory-mapped file by using a common name that is assigned by the process that created the file.</span></span>  
  
 <span data-ttu-id="a040f-118">Para trabalhar com um arquivo de mapeamento de memória, você deve criar uma exibição de todo o arquivo de memória mapeada ou parte dela.</span><span class="sxs-lookup"><span data-stu-id="a040f-118">To work with a memory-mapped file, you must create a view of the entire memory-mapped file or a part of it.</span></span> <span data-ttu-id="a040f-119">Você também pode criar vários modos de exibição para a mesma parte do arquivo de mapeamento de memória, criando assim simultâneas de memória.</span><span class="sxs-lookup"><span data-stu-id="a040f-119">You can also create multiple views to the same part of the memory-mapped file, thereby creating concurrent memory.</span></span> <span data-ttu-id="a040f-120">Dois modos de exibição permanecer simultâneas, precisam ser criados a partir do mesmo arquivo de memória mapeada.</span><span class="sxs-lookup"><span data-stu-id="a040f-120">For two views to remain concurrent, they have to be created from the same memory-mapped file.</span></span>  
  
 <span data-ttu-id="a040f-121">Vários modos de exibição também podem ser necessários se o arquivo for maior que o tamanho do espaço de memória lógica do aplicativo disponível para mapeamento (2 GB em um computador de 32 bits) de memória.</span><span class="sxs-lookup"><span data-stu-id="a040f-121">Multiple views may also be necessary if the file is greater than the size of the application’s logical memory space available for memory mapping (2 GB on a 32-bit computer).</span></span>  
  
 <span data-ttu-id="a040f-122">Há dois tipos de modos de exibição: modo de acesso e o modo de acesso aleatório de fluxo.</span><span class="sxs-lookup"><span data-stu-id="a040f-122">There are two types of views: stream access view and random access view.</span></span> <span data-ttu-id="a040f-123">Usar exibições de acesso de fluxo para acesso sequencial para um arquivo. Isso é recomendado para arquivos persistentes e IPC.</span><span class="sxs-lookup"><span data-stu-id="a040f-123">Use stream access views for sequential access to a file; this is recommended for non-persisted files and IPC.</span></span> <span data-ttu-id="a040f-124">Modos de exibição de acesso aleatório são preferenciais para trabalhar com arquivos persistentes.</span><span class="sxs-lookup"><span data-stu-id="a040f-124">Random access views are preferred for working with persisted files.</span></span>  
  
 <span data-ttu-id="a040f-125">Arquivos mapeados na memória são acessados por meio do Gerenciador de memória do sistema operacional, para que o arquivo é automaticamente particionado em um número de páginas e acessado conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="a040f-125">Memory-mapped files are accessed through the operating system’s memory manager, so the file is automatically partitioned into a number of pages and accessed as needed.</span></span> <span data-ttu-id="a040f-126">Você não precisa lidar com o gerenciamento de memória por conta própria.</span><span class="sxs-lookup"><span data-stu-id="a040f-126">You do not have to handle the memory management yourself.</span></span>  
  
 <span data-ttu-id="a040f-127">A ilustração a seguir mostra como vários processos podem ter vários e sobreposição de modos de exibição para o mesmo arquivo de mapeamento de memória ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="a040f-127">The following illustration shows how multiple processes can have multiple and overlapping views to the same memory-mapped file at the same time.</span></span>  
  
 <span data-ttu-id="a040f-128">![Modos de exibição mostra uma memória &#45; o arquivo mapeado. ] (../../../docs/standard/io/media/memmappersisted.png "MemMapPersisted")</span><span class="sxs-lookup"><span data-stu-id="a040f-128">![Shows views to a memory&#45;mapped file.](../../../docs/standard/io/media/memmappersisted.png "MemMapPersisted")</span></span>  
<span data-ttu-id="a040f-129">Várias e overlapped modos de exibição para um arquivo de memória mapeada</span><span class="sxs-lookup"><span data-stu-id="a040f-129">Multiple and overlapped views to a memory-mapped file</span></span>  
  
## <a name="programming-with-memory-mapped-files"></a><span data-ttu-id="a040f-130">Programando com arquivos mapeados na memória</span><span class="sxs-lookup"><span data-stu-id="a040f-130">Programming with Memory-Mapped Files</span></span>  
 <span data-ttu-id="a040f-131">A tabela a seguir fornece um guia para usar objetos de arquivos mapeados na memória e seus membros.</span><span class="sxs-lookup"><span data-stu-id="a040f-131">The following table provides a guide for using memory-mapped file objects and their members.</span></span>  
  
|<span data-ttu-id="a040f-132">Tarefa</span><span class="sxs-lookup"><span data-stu-id="a040f-132">Task</span></span>|<span data-ttu-id="a040f-133">Métodos ou propriedades a serem usadas</span><span class="sxs-lookup"><span data-stu-id="a040f-133">Methods or properties to use</span></span>|  
|----------|----------------------------------|  
|<span data-ttu-id="a040f-134">Para obter um <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objeto que representa um arquivo de mapeamento de memória persistente de um arquivo no disco.</span><span class="sxs-lookup"><span data-stu-id="a040f-134">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a persisted memory-mapped file from a file on disk.</span></span>|<span data-ttu-id="a040f-135">Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a040f-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="a040f-136">Para obter um <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objeto que representa um persistentes arquivo mapeado em memória (não associado a um arquivo no disco).</span><span class="sxs-lookup"><span data-stu-id="a040f-136">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a non-persisted memory-mapped file (not associated with a file on disk).</span></span>|<span data-ttu-id="a040f-137">Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a040f-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> method.</span></span><br /><br /> <span data-ttu-id="a040f-138">- ou -</span><span class="sxs-lookup"><span data-stu-id="a040f-138">- or -</span></span><br /><br /> <span data-ttu-id="a040f-139">Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a040f-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="a040f-140">Para obter um <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> objeto de um mapeamento de memória arquivo existente (persistente ou não persistente).</span><span class="sxs-lookup"><span data-stu-id="a040f-140">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object of an existing memory-mapped file (either persisted or non-persisted).</span></span>|<span data-ttu-id="a040f-141">Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a040f-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="a040f-142">Para obter um <xref:System.IO.UnmanagedMemoryStream> objeto para uma exibição acessado em sequência para o arquivo de mapeamento de memória.</span><span class="sxs-lookup"><span data-stu-id="a040f-142">To obtain a <xref:System.IO.UnmanagedMemoryStream> object for a sequentially accessed view to the memory-mapped file.</span></span>|<span data-ttu-id="a040f-143">Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a040f-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="a040f-144">Para obter um <xref:System.IO.UnmanagedMemoryAccessor> de objeto para um modo de exibição de acesso aleatório para uma memória mapeada CAM.</span><span class="sxs-lookup"><span data-stu-id="a040f-144">To obtain a <xref:System.IO.UnmanagedMemoryAccessor> object for a random access view to a memory-mapped fie.</span></span>|<span data-ttu-id="a040f-145">Método <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a040f-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="a040f-146">Para obter um <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> objeto a ser usado com código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a040f-146">To obtain a <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> object to use with unmanaged code.</span></span>|<span data-ttu-id="a040f-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType>propriedade.</span><span class="sxs-lookup"><span data-stu-id="a040f-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="a040f-148">- ou -</span><span class="sxs-lookup"><span data-stu-id="a040f-148">- or -</span></span><br /><br /> <span data-ttu-id="a040f-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>propriedade.</span><span class="sxs-lookup"><span data-stu-id="a040f-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="a040f-150">- ou -</span><span class="sxs-lookup"><span data-stu-id="a040f-150">- or -</span></span><br /><br /> <span data-ttu-id="a040f-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>propriedade.</span><span class="sxs-lookup"><span data-stu-id="a040f-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="a040f-152">Para atrasar a alocação de memória até que uma exibição é criada (somente arquivos não persistente).</span><span class="sxs-lookup"><span data-stu-id="a040f-152">To delay allocating memory until a view is created (non-persisted files only).</span></span><br /><br /> <span data-ttu-id="a040f-153">(Para determinar o tamanho de página atual do sistema, use o <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> propriedade.)</span><span class="sxs-lookup"><span data-stu-id="a040f-153">(To determine the current system page size, use the <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> property.)</span></span>|<span data-ttu-id="a040f-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A>método com o <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> valor.</span><span class="sxs-lookup"><span data-stu-id="a040f-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> method with the <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> value.</span></span><br /><br /> <span data-ttu-id="a040f-155">- ou -</span><span class="sxs-lookup"><span data-stu-id="a040f-155">- or -</span></span><br /><br /> <span data-ttu-id="a040f-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A>os métodos que possuem um <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeração como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a040f-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods that have a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeration as a parameter.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="a040f-157">Segurança</span><span class="sxs-lookup"><span data-stu-id="a040f-157">Security</span></span>  
 <span data-ttu-id="a040f-158">Você pode aplicar os direitos de acesso quando você cria um arquivo de mapeamento de memória, usando os seguintes métodos que usam um <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeração como um parâmetro:</span><span class="sxs-lookup"><span data-stu-id="a040f-158">You can apply access rights when you create a memory-mapped file, by using the following methods that take a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeration as a parameter:</span></span>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
-   <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="a040f-159">Você pode especificar os direitos de acesso para abrir um arquivo de mapeamento de memória existente usando o <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> métodos que usam um <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> como um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="a040f-159">You can specify access rights for opening an existing memory-mapped file by using the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> methods that take an <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> as a parameter.</span></span>  
  
 <span data-ttu-id="a040f-160">Além disso, você pode incluir um <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> objeto que contém as regras de acesso predefinidos.</span><span class="sxs-lookup"><span data-stu-id="a040f-160">In addition, you can include a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> object that contains predefined access rules.</span></span>  
  
 <span data-ttu-id="a040f-161">Para aplicar regras de acesso de novo ou alterado para um arquivo de mapeamento de memória, use o <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> método.</span><span class="sxs-lookup"><span data-stu-id="a040f-161">To apply new or changed access rules to a memory-mapped file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> method.</span></span> <span data-ttu-id="a040f-162">Para recuperar o acesso ou regras de um arquivo existente de auditoria, use o <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> método.</span><span class="sxs-lookup"><span data-stu-id="a040f-162">To retrieve access or audit rules from an existing file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a040f-163">Exemplos</span><span class="sxs-lookup"><span data-stu-id="a040f-163">Examples</span></span>  
  
### <a name="persisted-memory-mapped-files"></a><span data-ttu-id="a040f-164">Arquivos de memória mapeada persistentes</span><span class="sxs-lookup"><span data-stu-id="a040f-164">Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="a040f-165">O <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> métodos de criam um arquivo de mapeamento de memória de um arquivo existente no disco.</span><span class="sxs-lookup"><span data-stu-id="a040f-165">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> methods create a memory-mapped file from an existing file on disk.</span></span>  
  
 <span data-ttu-id="a040f-166">O exemplo a seguir cria uma exibição de mapeamento de memória de uma parte de um arquivo muito grande e manipula uma parte dele.</span><span class="sxs-lookup"><span data-stu-id="a040f-166">The following example creates a memory-mapped view of a part of an extremely large file and manipulates a portion of it.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
  
 <span data-ttu-id="a040f-167">O exemplo a seguir abre o mesmo arquivo de memória mapeada para outro processo.</span><span class="sxs-lookup"><span data-stu-id="a040f-167">The following example opens the same memory-mapped file for another process.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a><span data-ttu-id="a040f-168">Não persistente arquivos mapeados na memória</span><span class="sxs-lookup"><span data-stu-id="a040f-168">Non-Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="a040f-169">O <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> e <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> métodos criam um arquivo de mapeamento de memória que não está mapeado para um arquivo existente no disco.</span><span class="sxs-lookup"><span data-stu-id="a040f-169">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> and <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods create a memory-mapped file that is not mapped to an existing file on disk.</span></span>  
  
 <span data-ttu-id="a040f-170">O exemplo a seguir consiste em três processos separados (aplicativos de console) que gravar valores booleanos em um arquivo de mapeamento de memória.</span><span class="sxs-lookup"><span data-stu-id="a040f-170">The following example consists of three separate processes (console applications) that write Boolean values to a memory-mapped file.</span></span> <span data-ttu-id="a040f-171">A seguinte sequência de ações ocorrem:</span><span class="sxs-lookup"><span data-stu-id="a040f-171">The following sequence of actions occur:</span></span>  
  
1.  <span data-ttu-id="a040f-172">`Process A`cria o arquivo de mapeamento de memória e grava um valor para ele.</span><span class="sxs-lookup"><span data-stu-id="a040f-172">`Process A` creates the memory-mapped file and writes a value to it.</span></span>  
  
2.  <span data-ttu-id="a040f-173">`Process B`Abre o arquivo de mapeamento de memória e grava um valor para ele.</span><span class="sxs-lookup"><span data-stu-id="a040f-173">`Process B` opens the memory-mapped file and writes a value to it.</span></span>  
  
3.  <span data-ttu-id="a040f-174">`Process C`Abre o arquivo de mapeamento de memória e grava um valor para ele.</span><span class="sxs-lookup"><span data-stu-id="a040f-174">`Process C` opens the memory-mapped file and writes a value to it.</span></span>  
  
4.  <span data-ttu-id="a040f-175">`Process A`lê e exibe os valores do arquivo de mapeamento de memória.</span><span class="sxs-lookup"><span data-stu-id="a040f-175">`Process A` reads and displays the values from the memory-mapped file.</span></span>  
  
5.  <span data-ttu-id="a040f-176">Depois de `Process A` terminou com o arquivo de mapeamento de memória, o arquivo imediatamente é recuperado pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="a040f-176">After `Process A` is finished with the memory-mapped file, the file is immediately reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="a040f-177">Para executar este exemplo, faça o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a040f-177">To run this example, do the following:</span></span>  
  
1.  <span data-ttu-id="a040f-178">Compilar aplicativos e abra três janelas de Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="a040f-178">Compile the applications and open three Command Prompt windows.</span></span>  
  
2.  <span data-ttu-id="a040f-179">Na primeira janela de Prompt de comando, execute `Process A`.</span><span class="sxs-lookup"><span data-stu-id="a040f-179">In the first Command Prompt window, run `Process A`.</span></span>  
  
3.  <span data-ttu-id="a040f-180">Na segunda janela do Prompt de comando, execute `Process B`.</span><span class="sxs-lookup"><span data-stu-id="a040f-180">In the second Command Prompt window, run `Process B`.</span></span>  
  
4.  <span data-ttu-id="a040f-181">Retorne ao `Process A` e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="a040f-181">Return to `Process A` and press ENTER.</span></span>  
  
5.  <span data-ttu-id="a040f-182">Na terceira janela de Prompt de comando, execute `Process C`.</span><span class="sxs-lookup"><span data-stu-id="a040f-182">In the third Command Prompt window, run `Process C`.</span></span>  
  
6.  <span data-ttu-id="a040f-183">Retorne ao `Process A` e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="a040f-183">Return to `Process A` and press ENTER.</span></span>  
  
 <span data-ttu-id="a040f-184">A saída de `Process A` é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a040f-184">The output of `Process A` is as follows:</span></span>  
  
```  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 <span data-ttu-id="a040f-185">**Processo**</span><span class="sxs-lookup"><span data-stu-id="a040f-185">**Process A**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 <span data-ttu-id="a040f-186">**Processo B**</span><span class="sxs-lookup"><span data-stu-id="a040f-186">**Process B**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 <span data-ttu-id="a040f-187">**Processo C**</span><span class="sxs-lookup"><span data-stu-id="a040f-187">**Process C**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a040f-188">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a040f-188">See Also</span></span>  
 [<span data-ttu-id="a040f-189">E/S de arquivo e de fluxo</span><span class="sxs-lookup"><span data-stu-id="a040f-189">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)