---
title: Namespaces XAML e mapeamento de namespace para XAML WPF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom classes [WPF], mapping namespaces to
- XAML [WPF], namespaces
- namespace mapping [WPF]
- assemblies [WPF], mapping namespaces to
- mapping namespaces [WPF]
- XAML [WPF], namespace mapping
- classes [WPF], mapping namespaces to
- namespaces [WPF]
ms.assetid: 5c0854e3-7470-435d-9fe2-93eec9d3634e
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2798659d3b53cb32af8e5976d4fee69780266633
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a><span data-ttu-id="65d03-102">Namespaces XAML e mapeamento de namespace para XAML WPF</span><span class="sxs-lookup"><span data-stu-id="65d03-102">XAML Namespaces and Namespace Mapping for WPF XAML</span></span>
<span data-ttu-id="65d03-103">Este tópico oferece explicação adicional sobre a presença e a finalidade dos dois mapeamentos de namespace de XAML como frequentemente encontrados na marca raiz de um arquivo XAML do WPF.</span><span class="sxs-lookup"><span data-stu-id="65d03-103">This topic further explains the presence and purpose of the two XAML namespace mappings as often found in the root tag of a WPF XAML file.</span></span> <span data-ttu-id="65d03-104">Ele também descreve como gerar mapeamentos semelhantes para usar elementos que são definidos em seu próprio código e/ou em assemblies separados.</span><span class="sxs-lookup"><span data-stu-id="65d03-104">It also describes how to produce similar mappings for using elements that are defined in your own code, and/or within separate assemblies.</span></span>  
  
  
## <a name="what-is-a-xaml-namespace"></a><span data-ttu-id="65d03-105">O que é um Namespace de XAML?</span><span class="sxs-lookup"><span data-stu-id="65d03-105">What is a XAML Namespace?</span></span>  
 <span data-ttu-id="65d03-106">Um namespace de XAML é, na verdade, uma extensão do conceito de um namespace de XML.</span><span class="sxs-lookup"><span data-stu-id="65d03-106">A XAML namespace is really an extension of the concept of an XML namespace.</span></span> <span data-ttu-id="65d03-107">As técnicas para especificar um namespace de XAML contam com a sintaxe do namespace de XML, a convenção do uso de URIs como identificadores de namespace, o uso de prefixos para fornecer um meio para referenciar vários namespaces com base na mesma fonte de marcação e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="65d03-107">The techniques of specifying a XAML namespace rely on the XML namespace syntax, the convention of using URIs as namespace identifiers, using prefixes to provide a means to reference multiple namespaces from the same markup source, and so on.</span></span> <span data-ttu-id="65d03-108">O conceito principal que é adicionado à definição de XAML do namespace de XML é que um namespace de XAML implica tanto em um escopo de exclusividade para os usos de marcação como também influencia em como as entidades de marcação potencialmente contam com o suporte de namespaces específicos e assemblies referenciados do CLR.</span><span class="sxs-lookup"><span data-stu-id="65d03-108">The primary concept that is added to the XAML definition of the XML namespace is that a XAML namespace implies both a scope of uniqueness for the markup usages, and also influences how markup entities are potentially backed by specific CLR namespaces and referenced assemblies.</span></span> <span data-ttu-id="65d03-109">Essa última consideração também é influenciada pelo conceito de um contexto de esquema XAML.</span><span class="sxs-lookup"><span data-stu-id="65d03-109">This latter consideration is also influenced by the concept of a XAML schema context.</span></span> <span data-ttu-id="65d03-110">Mas, para fins de como o WPF funciona com namespaces de XAML, você geralmente pode pensar nos namespaces de XAML em termos de um namespace de XAML padrão, o namespace de linguagem XAML e quaisquer outros namespaces de XAML como mapeados pela sua marcação de XAML diretamente para namespaces e assemblies referenciados específicos com suporte do CLR.</span><span class="sxs-lookup"><span data-stu-id="65d03-110">But for purposes of how WPF works with XAML namespaces, you can generally think of XAML namespaces in terms of a default XAML namespace, the XAML language namespace, and any further XAML namespaces as mapped by your XAML markup directly to specific backing CLR namespaces and referenced assemblies.</span></span>  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>   
## <a name="the-wpf-and-xaml-namespace-declarations"></a><span data-ttu-id="65d03-111">As declarações de namespace de WPF e XAML</span><span class="sxs-lookup"><span data-stu-id="65d03-111">The WPF and XAML Namespace Declarations</span></span>  
 <span data-ttu-id="65d03-112">Dentro das declarações de namespace na marca raiz de muitos arquivos XAML, você verá que geralmente há duas declarações de namespace de XML.</span><span class="sxs-lookup"><span data-stu-id="65d03-112">Within the namespace declarations in the root tag of many XAML files, you will see that there are typically two XML namespace declarations.</span></span> <span data-ttu-id="65d03-113">A primeira declaração mapeia o namespace de XAML de cliente/estrutura geral do WPF como o padrão:</span><span class="sxs-lookup"><span data-stu-id="65d03-113">The first declaration maps the overall WPF client / framework XAML namespace as the default:</span></span>  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 <span data-ttu-id="65d03-114">A segunda declaração mapeia um namespace de XAML separado, mapeando-o (tipicamente) para o prefixo `x:`.</span><span class="sxs-lookup"><span data-stu-id="65d03-114">The second declaration maps a separate XAML namespace, mapping it (typically) to the `x:` prefix.</span></span>  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 <span data-ttu-id="65d03-115">A relação entre essas declarações é que o mapeamento de prefixo `x:` dá suporte aos intrínsecos que fazem parte da definição de linguagem XAML e o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é uma implementação que usa XAML como uma linguagem e define um vocabulário de seus objetos para XAML.</span><span class="sxs-lookup"><span data-stu-id="65d03-115">The relationship between these declarations is that the `x:` prefix mapping supports the intrinsics that are part of the XAML language definition, and [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] is one implementation that uses XAML as a language and defines a vocabulary of its objects for XAML.</span></span> <span data-ttu-id="65d03-116">Como os usos do vocabulário do WPF serão muito mais comuns que os usos de intrínsecos do XAML, o vocabulário do WPF é mapeado como o padrão.</span><span class="sxs-lookup"><span data-stu-id="65d03-116">Because the WPF vocabulary's usages will be far more common than the XAML intrinsics usages, the WPF vocabulary is mapped as the default.</span></span>  
  
 <span data-ttu-id="65d03-117">A convenção de prefixo `x:` para o mapeamento do suporte aos intrínsecos da linguagem XAML é seguida por modelos de projeto, código de exemplo e pela documentação dos recursos de linguagem dentro desse [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="65d03-117">The `x:` prefix convention for mapping the XAML language intrinsics support is followed by project templates, sample code, and the documentation of language features within this [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)].</span></span> <span data-ttu-id="65d03-118">O namespace de XAML define vários recursos comumente usados que são necessários até mesmo para aplicativos básicos do WPF.</span><span class="sxs-lookup"><span data-stu-id="65d03-118">The XAML namespace defines many commonly-used features that are necessary even for basic WPF  applications.</span></span> <span data-ttu-id="65d03-119">Por exemplo, para unir qualquer code-behind a um arquivo XAML por meio de uma classe parcial, você deve nomear essa classe como o atributo `x:Class` no elemento raiz do arquivo XAML relevante.</span><span class="sxs-lookup"><span data-stu-id="65d03-119">For instance, in order to join any code-behind to a XAML file through a partial class, you must name that class as the `x:Class` attribute in the root element of the relevant XAML file.</span></span> <span data-ttu-id="65d03-120">Ou, qualquer elemento, conforme definido em uma página XAML que você deseja acessar como um recurso com chave, deve ter o atributo `x:Key` definido no elemento em questão.</span><span class="sxs-lookup"><span data-stu-id="65d03-120">Or, any element as defined in a XAML page that you wish to access as a keyed resource should have the `x:Key` attribute set on the element in question.</span></span> <span data-ttu-id="65d03-121">Para obter mais informações sobre esses e outros aspectos do XAML, consulte [Visão geral de XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) ou [Sintaxe de XAML em detalhes](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).</span><span class="sxs-lookup"><span data-stu-id="65d03-121">For more information on these and other aspects of XAML see [XAML Overview (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) or [XAML Syntax In Detail](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).</span></span>  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>   
## <a name="mapping-to-custom-classes-and-assemblies"></a><span data-ttu-id="65d03-122">Mapeando para assemblies e classes personalizadas</span><span class="sxs-lookup"><span data-stu-id="65d03-122">Mapping to Custom Classes and Assemblies</span></span>  
 <span data-ttu-id="65d03-123">Você pode mapear namespaces de XML para assemblies usando uma série de tokens em um prefixo de declaração `xmlns`, de forma semelhante a como os namespaces de XAML padrão do WPF e intrínsecos de XAML são mapeados para prefixos.</span><span class="sxs-lookup"><span data-stu-id="65d03-123">You can map XML namespaces to assemblies using a series of tokens within an `xmlns` prefix declaration, similar to how the standard WPF and XAML-intrinsics XAML namespaces are mapped to prefixes.</span></span>  
  
 <span data-ttu-id="65d03-124">A sintaxe recebe os seguintes possíveis tokens nomeados e os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="65d03-124">The syntax takes the following possible named tokens and following values:</span></span>  
  
 <span data-ttu-id="65d03-125">`clr-namespace:` O namespace do CLR declarado dentro do assembly que contém os tipos públicos a serem expostos como elementos.</span><span class="sxs-lookup"><span data-stu-id="65d03-125">`clr-namespace:` The CLR namespace declared within the assembly that contains the public types to expose as elements.</span></span>  
  
 <span data-ttu-id="65d03-126">`assembly=` O assembly que contém parte ou todo o namespace do [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] referenciado.</span><span class="sxs-lookup"><span data-stu-id="65d03-126">`assembly=` The assembly that contains some or all of the referenced [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] namespace.</span></span> <span data-ttu-id="65d03-127">Esse valor é, geralmente, apenas o nome do assembly e não o caminho, e não inclui a extensão (como .dll ou .exe).</span><span class="sxs-lookup"><span data-stu-id="65d03-127">This value is typically just the name of the assembly, not the path, and does not include the extension (such as .dll or .exe).</span></span> <span data-ttu-id="65d03-128">O caminho para esse assembly deve ser estabelecido como uma referência de projeto no arquivo de projeto que contém o XAML que você está tentando mapear.</span><span class="sxs-lookup"><span data-stu-id="65d03-128">The path to that assembly must be established as a project reference in the project file that contains the XAML you are trying to map.</span></span> <span data-ttu-id="65d03-129">Para incorporar o controle de versão e a assinatura de nome forte, o `assembly` valor pode ser uma cadeia de caracteres, conforme definido pelo <xref:System.Reflection.AssemblyName>, em vez do nome de cadeia de caracteres simples.</span><span class="sxs-lookup"><span data-stu-id="65d03-129">In order to incorporate versioning and strong-name signing, the `assembly` value can be a string as defined by <xref:System.Reflection.AssemblyName>, rather than the simple string name.</span></span>  
  
 <span data-ttu-id="65d03-130">Observe que o caractere separando o token `clr-namespace` de seu valor é um dois-pontos (:) enquanto que o caractere que separa o token `assembly` de seu valor é um sinal de igual (=).</span><span class="sxs-lookup"><span data-stu-id="65d03-130">Note that the character separating the `clr-namespace` token from its value is a colon (:) whereas the character separating the `assembly` token from its value is an equals sign (=).</span></span> <span data-ttu-id="65d03-131">O caractere a ser usado entre esses dois tokens é um ponto e vírgula.</span><span class="sxs-lookup"><span data-stu-id="65d03-131">The character to use between these two tokens is a semicolon.</span></span> <span data-ttu-id="65d03-132">Além disso, não inclua nenhum espaço em branco em qualquer lugar na declaração.</span><span class="sxs-lookup"><span data-stu-id="65d03-132">Also, do not include any whitespace anywhere in the declaration.</span></span>  
  
### <a name="a-basic-custom-mapping-example"></a><span data-ttu-id="65d03-133">Um exemplo básico de mapeamento personalizado</span><span class="sxs-lookup"><span data-stu-id="65d03-133">A Basic Custom Mapping Example</span></span>  
 <span data-ttu-id="65d03-134">O código a seguir define uma classe personalizada de exemplo:</span><span class="sxs-lookup"><span data-stu-id="65d03-134">The following code defines an example custom class:</span></span>  
  
```csharp  
namespace SDKSample {  
    public class ExampleClass : ContentControl {  
        public ExampleClass() {  
        ...  
        }  
    }  
}  
```  
  
```vb  
Namespace SDKSample  
    Public Class ExampleClass  
        Inherits ContentControl  
         ...  
        Public Sub New()  
        End Sub  
    End Class  
End Namespace  
```  
  
 <span data-ttu-id="65d03-135">Essa classe personalizada é compilada em uma biblioteca, que é chamada de `SDKSampleLibrary` por configurações do projeto (não mostradas).</span><span class="sxs-lookup"><span data-stu-id="65d03-135">This custom class is then compiled into a library, which per the project settings (not shown) is named `SDKSampleLibrary`.</span></span>  
  
 <span data-ttu-id="65d03-136">Para fazer referência a essa classe personalizada, você também precisa incluí-la como uma referência para o projeto atual, o que você normalmente faria usando a interface do usuário do Gerenciador de Soluções no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="65d03-136">In order to reference this custom class, you also need to include it as a reference for your current project, which you would typically do using the Solution Explorer UI in Visual Studio.</span></span>  
  
 <span data-ttu-id="65d03-137">Agora que você tem uma biblioteca que contém uma classe e uma referência a ela nas configurações do projeto, você pode adicionar o seguinte mapeamento de prefixo como parte do seu elemento raiz no XAML:</span><span class="sxs-lookup"><span data-stu-id="65d03-137">Now that you have a library containing a class, and a reference to it in project settings, you can add the following prefix mapping as part of your root element in XAML:</span></span>  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 <span data-ttu-id="65d03-138">Para reunir tudo isso, abaixo está o XAML que inclui o mapeamento personalizado juntamente com o padrão típico e os mapeamentos de x: na marca raiz e que, em seguida, usa uma referência prefixada para instanciar a `ExampleClass` na interface do usuário:</span><span class="sxs-lookup"><span data-stu-id="65d03-138">To put it all together, the following is XAML that includes the custom mapping along with the typical default and x: mappings in the root tag, then uses a prefixed reference to instantiate `ExampleClass` in that UI:</span></span>  
  
```xaml  
<Page x:Class="WPFApplication1.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"   
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary">  
  ...  
  <custom:ExampleClass/>  
...  
</Page>  
```  
  
### <a name="mapping-to-current-assemblies"></a><span data-ttu-id="65d03-139">Mapeando para assemblies atuais</span><span class="sxs-lookup"><span data-stu-id="65d03-139">Mapping to Current Assemblies</span></span>  
 <span data-ttu-id="65d03-140">O `assembly` poderá ser omitido se o `clr-namespace` referenciado estiver sendo definido dentro do mesmo assembly como o código do aplicativo que faz referência às classes personalizadas.</span><span class="sxs-lookup"><span data-stu-id="65d03-140">`assembly` can be omitted if the `clr-namespace` referenced is being defined within the same assembly as the application code that is referencing the custom classes.</span></span> <span data-ttu-id="65d03-141">Ou, uma sintaxe equivalente para este caso é especificar `assembly=`, sem nenhum token de cadeia de caracteres após o sinal de igual.</span><span class="sxs-lookup"><span data-stu-id="65d03-141">Or, an equivalent syntax for this case is to specify `assembly=`, with no string token following the equals sign.</span></span>  
  
 <span data-ttu-id="65d03-142">As classes personalizadas não podem ser usadas como o elemento raiz de uma página se definidas no mesmo assembly.</span><span class="sxs-lookup"><span data-stu-id="65d03-142">Custom classes cannot be used as the root element of a page if defined in the same assembly.</span></span> <span data-ttu-id="65d03-143">As classes parciais não precisam ser mapeadas. Somente as classes que não são a classe parcial da página do seu aplicativo precisam ser mapeadas se você pretende referenciá-las como elementos no XAML.</span><span class="sxs-lookup"><span data-stu-id="65d03-143">Partial classes do not need to be mapped; only classes that are not the partial class of a page in your application need to be mapped if you intend to reference them as elements in XAML.</span></span>  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>   
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a><span data-ttu-id="65d03-144">Mapeando namespaces de CLR para namespaces de XML em um assembly</span><span class="sxs-lookup"><span data-stu-id="65d03-144">Mapping CLR Namespaces to XML Namespaces in an Assembly</span></span>  
 <span data-ttu-id="65d03-145">O WPF define um atributo de CLR que é consumido pelos processadores XAML para mapear vários namespaces de CLR para um único namespace de XAML.</span><span class="sxs-lookup"><span data-stu-id="65d03-145">WPF defines a CLR attribute that is consumed by XAML processors in order to map multiple CLR namespaces to a single XAML namespace.</span></span> <span data-ttu-id="65d03-146">Esse atributo, <xref:System.Windows.Markup.XmlnsDefinitionAttribute>, é colocado no nível de assembly no código-fonte que produz o assembly.</span><span class="sxs-lookup"><span data-stu-id="65d03-146">This attribute, <xref:System.Windows.Markup.XmlnsDefinitionAttribute>, is placed at the assembly level in the source code that produces the assembly.</span></span> <span data-ttu-id="65d03-147">O código de origem do assembly WPF usa esse atributo para mapear vários espaços de nomes comuns, como <xref:System.Windows> e <xref:System.Windows.Controls>, para o [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] namespace.</span><span class="sxs-lookup"><span data-stu-id="65d03-147">The WPF assembly source code uses this attribute to map the various common namespaces, such as <xref:System.Windows> and <xref:System.Windows.Controls>, to the [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] namespace.</span></span>  
  
 <span data-ttu-id="65d03-148">O <xref:System.Windows.Markup.XmlnsDefinitionAttribute> utiliza dois parâmetros: o nome do namespace XML/XAML e o nome do namespace CLR.</span><span class="sxs-lookup"><span data-stu-id="65d03-148">The <xref:System.Windows.Markup.XmlnsDefinitionAttribute> takes two parameters: the XML/XAML namespace name, and the CLR namespace name.</span></span> <span data-ttu-id="65d03-149">Mais de um <xref:System.Windows.Markup.XmlnsDefinitionAttribute> pode existir para mapear vários namespaces CLR para o mesmo namespace XML.</span><span class="sxs-lookup"><span data-stu-id="65d03-149">More than one <xref:System.Windows.Markup.XmlnsDefinitionAttribute> can exist to map multiple CLR namespaces to the same XML namespace.</span></span> <span data-ttu-id="65d03-150">Depois de mapeados, os membros desses namespaces também podem ser referenciados sem qualificação completa, se desejado, fornecendo a instrução `using` apropriada na página code-behind de classe parcial.</span><span class="sxs-lookup"><span data-stu-id="65d03-150">Once mapped, members of those namespaces can also be referenced without full qualification if desired by providing the appropriate `using` statement in the partial-class code-behind page.</span></span> <span data-ttu-id="65d03-151">Para obter mais detalhes, consulte <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="65d03-151">For more details, see <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.</span></span>  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a><span data-ttu-id="65d03-152">Namespaces de designer e outros prefixos de modelos de XAML</span><span class="sxs-lookup"><span data-stu-id="65d03-152">Designer Namespaces and Other Prefixes From XAML Templates</span></span>  
 <span data-ttu-id="65d03-153">Se você estiver trabalhando com ambientes de desenvolvimento e/ou com ferramentas de design para XAML do WPF, notará que há outros namespaces/prefixos de XAML definidos na marcação XAML.</span><span class="sxs-lookup"><span data-stu-id="65d03-153">If you are working with development environments and/or design tools for WPF XAML, you may notice that there are other defined XAML namespaces / prefixes within the XAML markup.</span></span>  
  
 <span data-ttu-id="65d03-154">O [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] usa um namespace de designer que é normalmente mapeado para o prefixo `d:`.</span><span class="sxs-lookup"><span data-stu-id="65d03-154">[!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] uses a designer namespace that is typically mapped to the prefix `d:`.</span></span> <span data-ttu-id="65d03-155">Os modelos de projeto mais recentes para WPF podem mapear previamente esse namespace de XAML para dar suporte ao intercâmbio do XAML entre o [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] e outros ambientes de design.</span><span class="sxs-lookup"><span data-stu-id="65d03-155">More recent project templates for WPF might pre-map this XAML namespace to support interchange of the XAML between [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] and other design environments.</span></span> <span data-ttu-id="65d03-156">Esse namespace de XAML de design é usado para manter o estado de design durante a movimentação da interface do usuário baseada em XAML no designer.</span><span class="sxs-lookup"><span data-stu-id="65d03-156">This design XAML namespace is used to perpetuate design state while roundtripping XAML-based UI in the designer.</span></span> <span data-ttu-id="65d03-157">Ele também é usado para recursos como `d:IsDataSource`, que habilitam fontes de dados em tempo de execução em um designer.</span><span class="sxs-lookup"><span data-stu-id="65d03-157">It is also used for features such as `d:IsDataSource`, which enable runtime data sources in a designer.</span></span>  
  
 <span data-ttu-id="65d03-158">Outro prefixo que talvez você veja mapeado é o `mc:`.</span><span class="sxs-lookup"><span data-stu-id="65d03-158">Another prefix you might see mapped is `mc:`.</span></span> <span data-ttu-id="65d03-159">O `mc:` é para a compatibilidade de marcação e aproveita um padrão de compatibilidade de marcação que não é, necessariamente, específico de XAML.</span><span class="sxs-lookup"><span data-stu-id="65d03-159">`mc:` is for markup compatibility, and is leveraging a markup compatibility pattern that is not necessarily XAML-specific.</span></span> <span data-ttu-id="65d03-160">Até certo ponto, os recursos de compatibilidade de marcação podem ser usados para a troca de XAML entre estruturas ou entre outros limites de implementação de suporte, para trabalhar entre contextos de esquema de XAML, para fornecer compatibilidade para modos limitados nos designers e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="65d03-160">To some extent, the markup compatibility features can be used to exchange XAML between frameworks or across other boundaries of backing implementation, work between XAML schema contexts, provide compatibility for limited modes in designers, and so on.</span></span> <span data-ttu-id="65d03-161">Para obter mais informações sobre os conceitos de compatibilidade de marcação e como eles se relacionam com o WPF, consulte [Recursos de linguagem de compatibilidade de marcação (mc:)](../../../../docs/framework/wpf/advanced/markup-compatibility-mc-language-features.md).</span><span class="sxs-lookup"><span data-stu-id="65d03-161">For more information on markup compatibility concepts and how they relate to WPF, see  [Markup Compatibility (mc:) Language Features](../../../../docs/framework/wpf/advanced/markup-compatibility-mc-language-features.md).</span></span>  
  
## <a name="wpf-and-assembly-loading"></a><span data-ttu-id="65d03-162">WPF e carregamento de assembly</span><span class="sxs-lookup"><span data-stu-id="65d03-162">WPF and Assembly Loading</span></span>  
 <span data-ttu-id="65d03-163">O contexto do esquema XAML para WPF integra-se com o modelo de aplicativo do WPF, que por sua vez, usa o conceito de CLR definido pelo <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="65d03-163">The XAML schema context for WPF integrates with the WPF application model, which in turn uses the CLR-defined concept of <xref:System.AppDomain>.</span></span> <span data-ttu-id="65d03-164">A sequência a seguir descreve como o contexto do esquema XAML interpreta como carregar assemblies ou localizar tipos em tempo de execução ou tempo de design, com base no uso de WPF <xref:System.AppDomain> e outros fatores.</span><span class="sxs-lookup"><span data-stu-id="65d03-164">The following sequence describes how XAML schema context interprets how to either load assemblies or find types at run time or design time, based on the WPF use of <xref:System.AppDomain> and other factors.</span></span>  
  
1.  <span data-ttu-id="65d03-165">Iterar por meio de <xref:System.AppDomain>, procurando um assembly já carregado que corresponde a todos os aspectos do nome, desde a última assembly carregado.</span><span class="sxs-lookup"><span data-stu-id="65d03-165">Iterate through the <xref:System.AppDomain>, looking for an already-loaded assembly that matches all aspects of the name, starting from the most recently loaded assembly.</span></span>  
  
2.  <span data-ttu-id="65d03-166">Se o nome é qualificado, chame <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> no nome qualificado.</span><span class="sxs-lookup"><span data-stu-id="65d03-166">If the name is qualified, call <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> on the qualified name.</span></span>  
  
3.  <span data-ttu-id="65d03-167">Se o nome curto + token de chave pública de um nome qualificado corresponder ao assembly do qual a marcação foi carregada, retorne esse assembly.</span><span class="sxs-lookup"><span data-stu-id="65d03-167">If the short name + public key token of a qualified name matches the assembly that the markup was loaded from, return that assembly.</span></span>  
  
4.  <span data-ttu-id="65d03-168">Use o nome curto + o token de chave pública para chamar <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65d03-168">Use the short name + public key token to call <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.</span></span>  
  
5.  <span data-ttu-id="65d03-169">Se o nome não qualificado, chame <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65d03-169">If the name is unqualified, call <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="65d03-170">O XAML livre não usa a etapa 3. Não há nenhum assembly do qual ele foi carregado.</span><span class="sxs-lookup"><span data-stu-id="65d03-170">Loose XAML does not use Step 3; there is no loaded-from assembly.</span></span>  
  
 <span data-ttu-id="65d03-171">Compilado XAML para WPF (gerado por meio de XamlBuildTask) não usa os assemblies já carregado de <xref:System.AppDomain> (etapa 1).</span><span class="sxs-lookup"><span data-stu-id="65d03-171">Compiled XAML for WPF (generated via XamlBuildTask) does not use the already-loaded assemblies from <xref:System.AppDomain> (Step 1).</span></span> <span data-ttu-id="65d03-172">Além disso, o nome nunca deve ser não qualificado na saída de XamlBuildTask, portanto, a etapa 5 não se aplica.</span><span class="sxs-lookup"><span data-stu-id="65d03-172">Also, the name should never be unqualified from XamlBuildTask output, so Step 5 does not apply.</span></span>  
  
 <span data-ttu-id="65d03-173">O BAML compilado (gerado por meio de PresentationBuildTask) usa todas as etapas, embora o BAML também não deva conter nomes de assembly não qualificados.</span><span class="sxs-lookup"><span data-stu-id="65d03-173">Compiled BAML (generated via PresentationBuildTask) uses all steps, although BAML also should not contain unqualified assembly names.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d03-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="65d03-174">See Also</span></span>  
 [<span data-ttu-id="65d03-175">Noções básicas sobre Namespaces XML</span><span class="sxs-lookup"><span data-stu-id="65d03-175">Understanding XML Namespaces</span></span>](http://go.microsoft.com/fwlink/?LinkId=98069)  
 [<span data-ttu-id="65d03-176">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="65d03-176">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)