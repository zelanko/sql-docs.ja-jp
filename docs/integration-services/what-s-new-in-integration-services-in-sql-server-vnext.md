---
title: "SQL Server vNext の Integration Services の新機能 | Microsoft Docs"
ms.custom: ""
ms.date: "03/16/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e26d7884-e772-46fa-bfdc-38567fe976a1
caps.latest.revision: 4
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 3
---
# SQL Server vNext の Integration Services の新機能
このトピックでは、[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] で追加または更新された機能について説明します。

>   [!NOTE] SQL Server vNext には、SQL Server 2016 の機能と、SQL Server 2016 更新プログラムで追加された機能も含まれています。 SQL Server 2016 の新しい SSIS 機能については、[「SQL Server 2016 で Integration Services の新機能」](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md) を参照してください。

## <a name="new-in-ssis-in-sql-server-vnext-ctp-11"></a>SQL Server vNext CTP 1.1 での SSIS の新機能

SQL Server vNext CTP 1.1 には、SSIS の新機能はありません。

## <a name="new-in-ssis-in-sql-server-vnext-ctp-10"></a>SQL Server vNext CTP 1.0 での SSIS の新機能

### <a name="scale-out-for-ssis"></a>SSIS のスケール アウト

スケール アウト機能により、複数のコンピューターで [!INCLUDE[ssIS_md](../includes/ssis-md.md)] を実行することが簡単になりました。 
   
Scale Out Master と Scale Out Worker をインストールすると、パッケージを配布し、さまざまな Worker で自動的に実行できます。 実行が予期せずに終了した場合、自動的に再試行されます。 また、Master を利用し、すべての実行と Worker が中央管理されます。
   
詳細については、[「Integration Services Scale Out」](../integration-services/integration-services-ssis-scale-out.md) を参照してください。
   
### <a name="support-for-microsoft-dynamics-online-resources"></a>Microsoft Dynamics オンライン リソースのサポート

OData ソースと OData 接続マネージャーで、Microsoft Dynamics AX Online と Microsoft Dynamics CRM Online の OData フィードに接続できるようになりました。
