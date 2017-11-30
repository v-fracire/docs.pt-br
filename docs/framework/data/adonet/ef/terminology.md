---
title: Terminologia do Entity Framework
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa2a1bd1-6118-487b-8673-eebc66b92945
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1e8207eb35d2bf4a62e02725d4cfff4303282cfd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="entity-framework-terminology"></a>Terminologia do Entity Framework
Este tópico define condições frequentemente referenciadas em [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] documentação. Os links são fornecidos para tópicos relevantes em que há informações adicionais disponíveis.  
  
|Termo|Definição|  
|----------|----------------|  
|associação|A definição de uma relação entre tipos de entidade.<br /><br /> Para obter mais informações, consulte [elemento Association (CSDL)](http://msdn.microsoft.com/en-us/c305169a-8af7-432f-9ba7-800a163aed41) e [tipo de associação](../../../../../docs/framework/data/adonet/association-type.md).|  
|conjunto de associações|Um contêiner lógico de instâncias de associações do mesmo tipo.<br /><br /> Para obter mais informações, consulte [elemento AssociationSet (CSDL)](http://msdn.microsoft.com/en-us/512cbb75-cebe-4f3f-970d-3419deeff684) e [conjunto de associações](../../../../../docs/framework/data/adonet/association-set.md).|  
|Code First|A partir do Entity Framework 4.1, você pode criar um modelo programaticamente usando o desenvolvimento Code First. Há dois cenários diferentes para desenvolvimento Code First. Em ambos os casos, o desenvolvedor define um modelo codificando definições de classe do .NET Framework e, em seguida, opcionalmente especifica o mapeamento adicional ou a configuração usando Anotações de Dados ou a API fluente.<br /><br /> Observe que o desenvolvimento do Code First é parte do [Entity Framework 5.0](http://go.microsoft.com/fwlink/?LinkId=234900). O Entity Framework 5.0 não faz parte do .NET Framework, mas é criado no .NET Framework 4.5. O Entity Framework 5.0 está disponível como a ['Do Entity Framework'](http://go.microsoft.com/fwlink/?LinkID=215714)[NuGet](http://go.microsoft.com/fwlink/?LinkId=232488) pacote. Para obter mais informações, consulte [versões do Entity Framework e controle de versão](http://go.microsoft.com/fwlink/?LinkId=234899).|  
|árvore de comandos|Uma representação programática comum de todos os [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] consultas que são compostas de uma ou mais expressões.<br /><br /> Para obter mais informações, consulte [visão geral do Entity Framework](../../../../../docs/framework/data/adonet/ef/overview.md).|  
|tipo complexo|Uma classe do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] que representa uma propriedade complexa conforme definida no modelo conceitual. Os tipos complexos permitem que as propriedades escalares sejam organizadas dentro das entidades. Os objetos complexos são instâncias de tipos complexos. Para obter mais informações, consulte [elemento ComplexType (CSDL)](http://msdn.microsoft.com/en-us/f1c2f311-9889-4b87-abd8-a94f322052e3) e [tipo complexo](../../../../../docs/framework/data/adonet/complex-type.md).|  
|ComplexType|A especificação de um tipo de dados que representa uma propriedade não escalar de um tipo de entidade que não tem uma propriedade de chave.<br /><br /> Para obter mais informações, consulte [elemento ComplexType (CSDL)](http://msdn.microsoft.com/en-us/f1c2f311-9889-4b87-abd8-a94f322052e3) e [tipo complexo](../../../../../docs/framework/data/adonet/complex-type.md).|  
|modelo conceitual|Uma especificação abstrata para os tipos de entidade, os tipos complexos, as associações, os contêineres de entidade, os conjuntos de entidades e os conjuntos de associações no domínio de um aplicativo no [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. O modelo conceitual é definido em CSDL no arquivo .csdl.<br /><br /> Para obter mais informações, consulte [de modelagem e mapeamento](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md).|  
|arquivo .csdl|Um arquivo XML que contém o modelo conceitual, expresso em CSDL.|  
|CSDL (linguagem de definição de esquema conceitual)|Um idioma baseado em XML que é usado para definir os tipos de entidade, as associações, os contêineres de entidade, os conjuntos de entidades e os conjuntos de associações de um modelo conceitual.<br /><br /> Para obter mais informações, consulte [especificação CSDL](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).|  
|contêiner|Um agrupamento lógico de conjuntos de entidades e associações.<br /><br /> Para obter mais informações, consulte [elemento EntityContainer (CSDL)](http://msdn.microsoft.com/en-us/06d03ecb-3b7a-4e7f-95d5-b95307d47a27) e [contêiner de entidade](../../../../../docs/framework/data/adonet/entity-container.md).|  
|simultaneidade|Um processo que permite que vários usuários acessem e alterem dados compartilhados simultaneamente. Por padrão, o [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] implementa um modelo de simultaneidade otimista.|  
|direção|Refere-se à natureza assimétrica de algumas associações. A direção é especificada com os atributos `FromRole` e `ToRole` de um elemento `NavigationProperty` ou `ReferentialConstraint` em um esquema.<br /><br /> Para obter mais informações, consulte [elemento NavigationProperty (CSDL)](http://msdn.microsoft.com/en-us/5829a238-a50e-4c81-901d-7b54fc00f27e) e [propriedade de navegação](../../../../../docs/framework/data/adonet/navigation-property.md).|  
|carregamento diligente|O processo de carregamento de um conjunto específico de objetos relacionados juntamente com os objetos que foram explicitamente solicitados na consulta.|  
|arquivo .edmx|Um arquivo XML que contém o modelo conceitual (em CSDL), o modelo de armazenamento (em SSDL) e os mapeamentos entre eles (em MSL). O arquivo. edmx é criado o [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] ferramentas. Para obter mais informações, consulte [. edmx visão geral do arquivo](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4).|  
|end|Uma entidade de participação em uma associação.<br /><br /> Para obter mais informações, consulte [elemento final (CSDL)](http://msdn.microsoft.com/en-us/04f3c141-95bc-424b-989b-1c071b449e7c) e [end de associação](../../../../../docs/framework/data/adonet/association-end.md).|  
|entidade|Um conceito no domínio de um aplicativo no qual um tipo de dados é definido.<br /><br /> Para obter mais informações, consulte [elemento EntityType (CSDL)](http://msdn.microsoft.com/en-us/19562e9f-fd70-4b59-bc15-3e289cbb6054) e [tipo de entidade](../../../../../docs/framework/data/adonet/entity-type.md).|  
|EntityClient|Um provedor de dados do [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] independente de armazenamento que contém classes como `EntityConnection`, `EntityCommand` e `EntityDataReader`. Funciona com [!INCLUDE[esql](../../../../../includes/esql-md.md)] e se conecta ao armazenamento específico [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] provedores de dados, como `SqlClient`.<br /><br /> Para obter mais informações, consulte [provedor EntityClient para Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).|  
|contêiner da entidade|Especifica os conjuntos de entidades e associações que serão implementados em um namespace especificado.<br /><br /> Para obter mais informações, consulte [elemento EntityContainer (CSDL)](http://msdn.microsoft.com/en-us/06d03ecb-3b7a-4e7f-95d5-b95307d47a27) e [contêiner de entidade](../../../../../docs/framework/data/adonet/entity-container.md).|  
|Modelo de Dados de Entidade (EDM)|Um conjunto de conceitos que descrevem a estrutura dos dados, como entidades e relações, independentemente do seu formato de armazenamento.<br /><br /> Para obter mais informações, consulte [modelo de dados de entidade](../../../../../docs/framework/data/adonet/entity-data-model.md).|  
|Entity Framework|Um conjunto de tecnologias que oferece suporte ao desenvolvimento de aplicativos de software orientados a dados, permitindo que os desenvolvedores trabalhem com modelos conceituais mapeados para esquemas lógicos nas fontes de dados.<br /><br /> Para obter mais informações, consulte [visão geral do Entity Framework](../../../../../docs/framework/data/adonet/ef/overview.md).|  
|conjunto de entidades|Um contêiner lógico de entidades de um tipo específico e seus subtipos. Conjuntos de entidades mapeados para tabelas em um banco de dados.<br /><br /> Para obter mais informações, consulte [elemento EntitySet (CSDL)](http://msdn.microsoft.com/en-us/ec56db77-718d-4c0e-adc9-f1d33c896287) e [conjunto de entidades](../../../../../docs/framework/data/adonet/entity-set.md).|  
|Entity SQL|Um dialeto da linguagem SQL independente de armazenamento que trabalha diretamente com esquemas de entidade conceituais e oferece suporte a conceitos de modelo conceitual, como herança e relações.<br /><br /> Para obter mais informações, consulte [linguagem Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md).|  
|tipo de entidade|Uma classe do [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] que representa uma entidade conforme definida no modelo conceitual. Os tipos de entidade podem ter propriedades escalares, complexas e de navegação. Os objetos são instâncias de tipos de entidade. Para obter mais informações, consulte [trabalhando com objetos](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).|  
|EntityType|A especificação de um tipo de dados que inclui uma chave e um conjunto de propriedades nomeado, e que representa um item de nível superior em um modelo conceitual ou em um modelo de armazenamento.<br /><br /> Para obter mais informações, consulte [elemento EntityType (CSDL)](http://msdn.microsoft.com/en-us/19562e9f-fd70-4b59-bc15-3e289cbb6054) e [tipo de entidade](../../../../../docs/framework/data/adonet/entity-type.md).|  
|carregamento explícito|Quando os objetos são retornados por uma consulta, os objetos relacionados não são carregados ao mesmo tempo. Por padrão, eles só são carregados até que solicitado explicitamente por meio do método `Load` em uma propriedade de navegação.|  
|associação de chave estrangeira|Uma associação entre entidades que é gerenciada através das propriedades de chave estrangeira.|  
|relação de identificação|Uma relação em que a chave primária da entidade de segurança é parte da chave primária da entidade dependente. Nesse tipo de relação, a entidade dependente não pode existir sem a entidade de segurança.|  
|associação independente|Uma associação entre entidades que é representada e controlada por um objeto independente.|  
|key|O atributo de um tipo de entidade que especifica qual propriedade ou conjunto de propriedades será usado para identificar instâncias exclusivas do tipo de entidade. Representado na camada de objeto pela classe <xref:System.Data.EntityKey>.<br /><br /> Para obter mais informações, consulte [chave de elemento (CSDL)](http://msdn.microsoft.com/en-us/0cdb1402-dbc7-4a04-a11e-5729cdf7431b) e [chave da entidade](../../../../../docs/framework/data/adonet/entity-key.md).|  
|carregamento diferido|Quando os objetos são retornados por uma consulta, os objetos relacionados não são carregados ao mesmo tempo. Em vez disso, eles são carregados automaticamente quando a propriedade de navegação é acessada.|  
|[!INCLUDE[linq_entities](../../../../../includes/linq-entities-md.md)]|Uma sintaxe de consulta que define um conjunto de operadores de consulta que permite operações de passagem, de filtro e de projeção a serem expressas de forma direta e declarativa no [!INCLUDE[csprcs](../../../../../includes/csprcs-md.md)] e no [!INCLUDE[vbprvb](../../../../../includes/vbprvb-md.md)].<br /><br /> Para obter mais informações, consulte [LINQ to Entities](../../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md).|  
|mapeamento|Uma especificação das correspondências entre itens de um modelo conceitual e itens de um modelo de armazenamento.<br /><br /> Para obter mais informações, consulte [especificação de MSL](../../../../../docs/framework/data/adonet/ef/language-reference/msl-specification.md).|  
|arquivo .msl|Um arquivo XML que contém o mapeamento entre o modelo conceitual e o modelo de armazenamento, expresso em MSL.|  
|MSL (linguagem de especificação de mapeamento)|Uma linguagem baseada em XML usada para mapear itens definidos em um modelo conceitual para itens de um modelo de armazenamento.<br /><br /> Para obter mais informações, consulte [especificação de MSL](../../../../../docs/framework/data/adonet/ef/language-reference/msl-specification.md).|  
|funções de modificação|Procedimentos armazenados que são usados para inserir, atualizar e excluir os dados que estão na fonte de dados. Essas funções são usadas no lugar dos comandos gerados do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. As funções de modificação são definidas pelo elemento `Function` no modelo de armazenamento. O [ModificationFunctionMapping](http://msdn.microsoft.com/en-us/b44b5b13-9937-448b-ba36-7a0cfefea782) elemento mapeia essas funções de modificação para inserir, atualizar e excluir operações em entidades que são definidas no modelo conceitual.|  
|multiplicidade|O número de entidades que podem existir em cada lado de uma relação, conforme definido por uma associação. Também conhecido como cardinalidade.<br /><br /> Para obter mais informações, consulte [elemento final (CSDL)](http://msdn.microsoft.com/en-us/04f3c141-95bc-424b-989b-1c071b449e7c) e [end de associação](../../../../../docs/framework/data/adonet/association-end.md).|  
|vários conjuntos de entidades por tipo|A capacidade de um tipo de entidade a ser definido em mais de um conjunto de entidades.<br /><br /> Para obter mais informações, consulte [elemento EntitySet (CSDL)](http://msdn.microsoft.com/en-us/ec56db77-718d-4c0e-adc9-f1d33c896287) e [como: definir um modelo com vários conjuntos de entidades por tipo](http://msdn.microsoft.com/en-us/61aa4fca-5ac0-4f47-9bc8-46e8c2965ef7).|  
|propriedade de navegação|A propriedade de um tipo de entidade que representa uma relação com outro tipo de entidade, conforme definido por uma associação. As propriedades de navegação são usadas para retornar objetos relacionados como <xref:System.Data.Objects.DataClasses.EntityCollection%601> ou <xref:System.Data.Objects.DataClasses.EntityReference%601>, dependendo da multiplicidade na outra extremidade da associação.<br /><br /> Para obter mais informações, consulte [elemento NavigationProperty (CSDL)](http://msdn.microsoft.com/en-us/5829a238-a50e-4c81-901d-7b54fc00f27e) e [propriedade de navegação](../../../../../docs/framework/data/adonet/navigation-property.md).|  
|caminhos de consulta|A representação de cadeia de caracteres de um caminho que especifica quais objetos serão retornados quando uma consulta de objeto for executada. Um caminho de consulta é definido chamando o método <xref:System.Data.Objects.ObjectQuery%601.Include%2A> em <xref:System.Data.Objects.ObjectQuery%601>.<br /><br /> Para obter mais informações, consulte [objetos relacionados ao carregar](http://msdn.microsoft.com/en-us/452347d2-7b3b-44cd-9001-231299a28cb1).|  
|contexto de objeto|Representa o contêiner de entidade definido no modelo conceitual. Ele contém uma conexão com a fonte de dados subjacente e fornece serviços como controle de alterações e resolução de identidade. Um contexto de objeto é representado por uma instância da classe <xref:System.Data.Objects.ObjectContext> ou `DbContext`.<br /><br /> `DbContext`é parte do [Entity Framework 5.0](http://go.microsoft.com/fwlink/?LinkId=234900). O Entity Framework 5.0 não faz parte do .NET Framework, mas é criado no .NET Framework 4.5. O Entity Framework 5.0 está disponível como a ['Do Entity Framework'](http://go.microsoft.com/fwlink/?LinkID=215714)[NuGet](http://go.microsoft.com/fwlink/?LinkId=232488) pacote. Para obter mais informações, consulte [versões do Entity Framework e controle de versão](http://go.microsoft.com/fwlink/?LinkId=234899).|  
|camada de objeto|Os tipos de entidade e as definições de contexto de objeto usados pelo Entity Framework.|  
|consulta de objeto|Uma consulta executada em um contexto de objeto em um modelo conceitual que retorna dados como objetos.<br /><br /> Para obter mais informações, consulte [consultas de objeto](http://msdn.microsoft.com/en-us/0768033c-876f-471d-85d5-264884349276).|  
|mapeamento relacional de objeto|Uma técnica para transformar dados de um banco de dados relacional em tipos de dados que podem ser usados em aplicativos de software orientados a objeto.<br /><br /> O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] fornece serviços de mapeamento relacional de objeto mapeando dados relacionais, conforme definido no modelo de armazenamento, para tipos de dados, conforme definido no modelo conceitual.<br /><br /> Para obter mais informações, consulte [de modelagem e mapeamento](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md).|  
|Serviços de Objeto|Os serviços fornecidos pelo [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] que permitem que o código do aplicativo operar em entidades, como [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] objetos.|  
|objeto com ignorância de persistência|Um objeto que não contém nenhuma lógica relacionada ao armazenamento de dados. Também conhecido como entidade POCO.|  
|POCO|Objeto CLR antigo simples. Um objeto que não herda de outra classe nem implementa uma interface.|  
|entidade POCO|Uma entidade do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] que não herda do <xref:System.Data.Objects.DataClasses.EntityObject> nem do <xref:System.Data.Objects.DataClasses.ComplexObject> e não implementa a interface do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Frequentemente, as entidades POCO existentes objetos de domínio que você use um [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] aplicativo. Essas entidades oferecem suporte à ignorância de persistência. Para obter mais informações, consulte [trabalhando com entidades POCO](http://msdn.microsoft.com/en-us/5e0fb82a-b6d1-41a1-b37b-c12db61629d3).|  
|objeto proxy|Um objeto derivado de uma classe POCO e gerado pelo [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] para oferecer suporte ao controle de alterações e ao carregamento diferido. Para obter mais informações, consulte [requisitos para a criação de Proxies POCO](http://msdn.microsoft.com/en-us/dcdbf982-9b9d-4582-806a-64de4a1c03c8).|  
|restrição referencial|Uma restrição definida em um modelo conceitual que indica que uma entidade tem uma relação dependente com outra entidade. Essa restrição significa que a instância de uma entidade dependente não pode existir sem uma instância correspondente da entidade de segurança<br /><br /> Para obter mais informações, consulte [ReferentialConstraint elemento (CSDL)](http://msdn.microsoft.com/en-us/24f96a80-85b5-4f2e-a14c-0e3eb6796fa0) e [restrição de integridade referencial](../../../../../docs/framework/data/adonet/referential-integrity-constraint.md).|  
|relação|Uma conexão lógica entre entidades.|  
|função|O nome fornecido para cada `End` de uma associação para esclarecer a semântica da relação.<br /><br /> Para obter mais informações, consulte [elemento final (CSDL)](http://msdn.microsoft.com/en-us/04f3c141-95bc-424b-989b-1c071b449e7c) e [end de associação](../../../../../docs/framework/data/adonet/association-end.md).|  
|propriedade escalar|A propriedade de uma entidade que é mapeada para um único campo no modelo de armazenamento.|  
|entidade de rastreamento automático|Uma entidade criada a partir de um kit de ferramentas de transformação do modelo de texto (T4) que tem a capacidade de registrar alterações em propriedades escalares, complexas e de navegação.|  
|tipo simples|Um tipo primitivo que é usado definir propriedades no modelo conceitual.<br /><br /> Para obter mais informações, consulte [tipos de modelo conceitual (CSDL)](http://msdn.microsoft.com/en-us/987b995f-e429-4569-9559-b4146744def4) e [modelo de dados de entidade: tipos de dados primitivos](../../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).|  
|entidade de divisão|Um tipo de entidade mapeado para dois tipos separados no modelo de armazenamento.<br /><br /> Para obter mais informações, consulte [como: definir um modelo com uma única entidade mapeada para duas tabelas](http://msdn.microsoft.com/en-us/01762517-e4ab-439d-99e6-564ab7d6f3ed).|  
|modelo de armazenamento|Uma definição do modelo lógico de dados em uma fonte de dados com suporte, como um banco de dados relacional. O modelo de armazenamento é definido em SSDL no arquivo .ssdl.<br /><br /> Para obter mais informações, consulte [de modelagem e mapeamento](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md) e [especificação de SSDL](../../../../../docs/framework/data/adonet/ef/language-reference/ssdl-specification.md).|  
|arquivo .ssdl|Um arquivo XML que contém o modelo de armazenamento, expresso em SSDL.|  
|SSDL (linguagem de definição de esquema repositório)|Uma linguagem baseada em XML usada para definir os tipos de entidade, as associações, os contêineres de entidade, os conjuntos de entidades e os conjuntos de associações de um modelo de armazenamento que corresponde frequentemente a um esquema de banco de dados.<br /><br /> Para obter mais informações, consulte [especificação de SSDL](../../../../../docs/framework/data/adonet/ef/language-reference/ssdl-specification.md).|  
|tabela por hierarquia|Um método de modelagem de uma hierarquia de tipo em um banco de dados que inclui os atributos de todos os tipos da hierarquia em uma tabela.|  
|tabela por tipo|Um método de modelagem de uma hierarquia de tipo em um banco de dados que usa várias tabelas com relações um-para-um para modelar os vários tipos.|  
  
## <a name="see-also"></a>Consulte também  
 [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)  
 [Visão geral do Entity Framework](../../../../../docs/framework/data/adonet/ef/overview.md)  
 [Introdução](../../../../../docs/framework/data/adonet/ef/getting-started.md)  
 [Recursos do Entity Framework](../../../../../docs/framework/data/adonet/ef/resources.md)