---
title: "[アクティブな操作] ダイアログ ボックス | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.ssms.isoperations.executions.f1"
  - "sql13.ssis.ssms.isoperations.general.f1"
ms.assetid: 5bb0fcd6-0ce9-488a-85b8-25dddaa03cda
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# [アクティブな操作] ダイアログ ボックス
  配置、検証、パッケージの実行など、** サーバー上で現在実行中の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 操作の状態を表示するには、**[アクティブな操作][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ダイアログ ボックスを使用します。 このデータは、SSISDB カタログに格納されます。  
  
 関連 [!INCLUDE[tsql](../../includes/tsql-md.md)] ビューの詳細については、「[catalog.operations (SSISDB データベース)](../../integration-services/system-views/catalog-operations-ssisdb-database.md)」、「[catalog.validations (SSISDB データベース)](../../integration-services/system-views/catalog-validations-ssisdb-database.md)」、「[catalog.executions (SSISDB データベース)](../../integration-services/system-views/catalog-executions-ssisdb-database.md)」を参照してください。  
  
 **目的に合ったトピックをクリックしてください**  
  
-   [[アクティブな操作] ダイアログ ボックスを開く](../Topic/Active%20Operations%20Dialog%20Box.md#open_dialog)  
  
-   [オプション](#options)  
  
##  <a name="open_dialog"></a> [アクティブな操作] ダイアログ ボックスを開く  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] を開きます。  
  
2.  Microsoft SQL Server データベース エンジンに接続します。  
  
3.  オブジェクト エクスプローラーで、**[Integration Services]** ノードを展開します。**[SSISDB]** を右クリックし、**[アクティブな操作]** をクリックします。  
  
## オプションの構成  
  
###  <a name="options"></a> オプション  
 **型**  
 操作の種類を指定します。 **[種類]** フィールドに指定できる値、および Transact-SQL の **catalog.operations** ビューに含まれる operations_type 列の対応する値を次に示します。  
  
|||  
|-|-|  
|Integration Services の初期化|1|  
|操作のクリーンアップ (SQL エージェント ジョブ)|2|  
|プロジェクト バージョンのクリーンアップ (SQL エージェント ジョブ)|3|  
|プロジェクトの配置|101|  
|プロジェクトの復元|106|  
|パッケージ実行の作成および開始|200|  
|操作の停止 (検証または実行の停止)|202|  
|プロジェクトの検証|300|  
|パッケージの検証|301|  
|カタログの構成|1000|  
  
 **[停止]**  
 現在実行中の操作を停止する場合にクリックします。  
  
  