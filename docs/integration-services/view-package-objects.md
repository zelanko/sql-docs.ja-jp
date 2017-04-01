---
title: "パッケージ オブジェクトを表示する | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Integration Services パッケージ、プロパティ"
  - "プロパティ [Integration Services]"
  - "[パッケージ エクスプローラー] ウィンドウ [Integration Services]"
  - "パッケージ [Integration Services]、プロパティ"
  - "エクスプローラー ビュー [Integration Services]"
  - "SSIS パッケージ、プロパティ"
  - "パッケージ オブジェクトの表示"
  - "SQL Server Integration Services パッケージ、プロパティ"
ms.assetid: a85c0245-0a68-4eb0-83b1-9b11df80bd10
caps.latest.revision: 36
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 35
---
# パッケージ オブジェクトを表示する
  [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーでは、 **[パッケージ エクスプローラー]** タブで、パッケージをエクスプローラー表示できます。 この表示には、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] アーキテクチャのコンテナー階層が反映されます。 パッケージ コンテナーはこの階層の最上層にあり、パッケージを展開すると、そのパッケージ内にある接続、実行可能ファイル、イベント ハンドラー、ログ プロバイダー、優先順位制約、および変数が表示されます。  
  
 実行可能ファイルとは、パッケージ内のコンテナーおよびタスクのことで、イベント ハンドラー、優先順位制約、および変数を含めることができます。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では、入れ子構造の階層のコンテナーがサポートされているため、For ループ コンテナー、Foreach ループ コンテナー、およびシーケンス コンテナーは他の実行可能ファイルを含めることができます。  
  
 パッケージにデータ フローが含まれる場合、 **パッケージ エクスプローラー** にはデータ フロー タスクが一覧表示され、データ フロー コンポーネントを一覧表示する **[コンポーネント]** フォルダーが含まれます。  
  
 **[パッケージ エクスプローラー]** タブでは、パッケージ内のオブジェクトを削除したり、 **[プロパティ]** ウィンドウにアクセスしてオブジェクトのプロパティを表示できます。  
  
 次の図は、簡単なパッケージのツリー ビューを示しています。  
  
 ![[パッケージ エクスプローラー] タブのスクリーンショット](../integration-services/media/packageexplorer.gif "[パッケージ エクスプローラー] タブのスクリーンショット")  
  
### パッケージの内容を表示するには  
  
-   [パッケージ エクスプローラーでパッケージ オブジェクトを表示する](../Topic/View%20Package%20Objects%20in%20Package%20Explorer.md)  
  
## 参照  
 [Integration Services タスク](../integration-services/control-flow/integration-services-tasks.md)   
 [Integration Services コンテナー](../integration-services/control-flow/integration-services-containers.md)   
 [優先順位制約](../integration-services/control-flow/precedence-constraints.md)   
 [Integration Services (SSIS) の変数](../integration-services/integration-services-ssis-variables.md)   
 [Integration Services (SSIS) のイベント ハンドラー](../integration-services/integration-services-ssis-event-handlers.md)   
 [Integration Services (SSIS) のログ記録](../integration-services/performance/integration-services-ssis-logging.md)  
  
  