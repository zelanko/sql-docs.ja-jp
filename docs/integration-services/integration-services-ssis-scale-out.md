---
title: "Integration Services (SSIS) Scale Out | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dcfbd1c5-c001-4fb7-b9ae-916e49ab6a96
caps.latest.revision: 6
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 6
---
# Integration Services (SSIS) Scale Out
[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Scale Out では、実行を複数のコンピューターに分散することで、パッケージを高いパフォーマンスで実行できます。 SQL Server Management Studio では、複数のパッケージの実行の要求を送信することができます。 これらのパッケージは、Scale Out モードで並列実行されます。  


## <a name="ssis-scale-out-master-and-scale-out-worker"></a>SSIS の Scale Out Master と Scale Out Worker
[!INCLUDE[ssIS_md](../includes/ssis-md.md)] Scale Out は、1 つの [!INCLUDE[ssIS_md](../includes/ssis-md.md)] Scale Out Master といくつかの [!INCLUDE[ssIS_md](../includes/ssis-md.md)] Scale Out Worker で構成されます。 Scale Out Master は、Scale Out の管理を担当し、ユーザーからパッケージの実行要求を受け取ります。 Scale Out Worker は、Scale Out Master から実行作業をプルし、パッケージの実行作業を実行します。 詳細については、「[Scale Out Master](../integration-services/integration-services-ssis-scale-out-master.md)」と「[Scale Out Worker](../integration-services/integration-services-ssis-scale-out-worker.md)」を参照してください。


## <a name="how-to-set-up-scale-out"></a>Scale Out を設定する方法
[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Scale Out は、Scale Out Master および Scale Out Worker が 1 台のコンピューター上に共存するようセットアップされているコンピューターで実行できます。 Scale Out は、Scale Out Worker がそれぞれ別のコンピューターに配置された複数のコンピューターで実行することも可能です。
- [チュートリアル: Integration Services Scale Out をセットアップする](../integration-services/walkthrough-set-up-integration-services-scale-out.md)


## <a name="run-packages-in-scale-out"></a>Scale Out でのパッケージの実行
Scale Out では、SSISDB カタログの複数のパッケージを並列で実行できます。 詳細については、[「Integration Services (SSIS) Scale Out でパッケージを実行する」](../integration-services/run-packages-in-integration-services-ssis-scale-out.md)をご覧ください。

