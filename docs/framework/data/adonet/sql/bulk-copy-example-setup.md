---
title: Configuração de exemplo de cópia em massa
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: 71daf489fdf5e7e12594e798bc3ac01b1c76b027
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402370"
---
# <a name="bulk-copy-example-setup"></a>Configuração de exemplo de cópia em massa
O <xref:System.Data.SqlClient.SqlBulkCopy> classe pode ser usado para gravar dados somente em tabelas do SQL Server. Os exemplos de código mostrados neste tópico usam o banco de dados de exemplo do SQL Server, **AdventureWorks**. Para evitar a alteração das tabelas existentes a exemplos de código gravam dados em tabelas que você deve criar primeiro.  
  
 O **BulkCopyDemoMatchingColumns** e **BulkCopyDemoDifferentColumns** tabelas são baseadas no **AdventureWorks** **Production**  tabela. Nos exemplos de código que usam essas tabelas, os dados são adicionados dos **Production** tabela para uma dessas tabelas de exemplo. O **BulkCopyDemoDifferentColumns** tabela é usada quando o exemplo ilustra como mapear colunas de dados de origem para a tabela de destino; **BulkCopyDemoMatchingColumns** é usado para a maioria dos outros exemplos.  
  
 Alguns dos exemplos de código demonstram como usar um <xref:System.Data.SqlClient.SqlBulkCopy> classe para gravar em várias tabelas. Para esses exemplos, o **BulkCopyDemoOrderHeader** e **BulkCopyDemoOrderDetail** tabelas são usadas como tabelas de destino. Essas tabelas são baseadas na **Sales. SalesOrderHeader** e **Sales. SalesOrderDetail** tabelas na **AdventureWorks**.  
  
> [!NOTE]
>  O **SqlBulkCopy** exemplos de código são fornecidos para demonstrar a sintaxe para usar **SqlBulkCopy** somente. Se as tabelas de origem e destino estiverem localizadas na mesma instância do SQL Server, é mais fácil e rápido para usar um Transact-SQL `INSERT … SELECT` instrução para copiar os dados.  
  
## <a name="table-setup"></a>Configuração da tabela  
 Para criar as tabelas necessárias para os exemplos de código seja executado corretamente, você deve executar as seguintes instruções Transact-SQL em um banco de dados do SQL Server.  
  
```  
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED  
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED  
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
```  
  
## <a name="see-also"></a>Consulte também  
 [Operações de cópia em massa no SQL Server](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
