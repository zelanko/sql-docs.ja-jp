---
title: "統計の更新タスク | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.updatestatisticstask.f1"
helpviewer_keywords: 
  - "更新、統計"
  - "統計の更新タスク [Integration Services]"
ms.assetid: 0247483b-f092-4511-8fa8-3610108bd1bc
caps.latest.revision: 45
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 45
---
# 統計の更新タスク
  統計の更新タスクは、指定されたテーブルまたはインデックス付きビュー内の 1 つ以上の統計グループ (コレクション) についてキー値の分布に関する情報を更新します。 詳細については、「 [Statistics](../../relational-databases/statistics/statistics.md)」を参照してください。  
  
 統計の更新タスクを使用すると、パッケージは単一データベースまたは複数のデータベース内の統計を更新できます。 このタスクにより単一データベース内の統計のみを更新する場合、タスクによって統計を更新するビューおよびテーブルを選択できます。 更新は、すべての統計、列統計のみ、またはインデックス統計のみを対象とするように構成できます。  
  
 このタスクは、次の引数および句を含めて UPDATE STATISTICS ステートメントをカプセル化します。  
  
-   *table_name* または *view_name* 引数。  
  
-   すべての統計に更新が適用される場合、暗黙的に WITH ALL 句が含められます。  
  
-   列統計にのみ更新が適用される場合、WITH COLUMN 句が含められます。  
  
-   インデックス統計にのみ更新が適用される場合、WITH INDEX 句が含められます。  
  
 統計の更新タスクにより複数データベース内の統計を更新する場合、タスクは複数の UPDATE STATISTICS ステートメントを各テーブルまたはビューに対して 1 つずつ実行します。 UPDATE STATISTICS の全インスタンスで同じ句が使用されますが、*table_name* または *view_name* の値が異なります。 詳細については、「[CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md)」および「[UPDATE STATISTICS (Transact-SQL)](../../t-sql/statements/update-statistics-transact-sql.md)」を参照してください。  
  
> [!IMPORTANT]  
>  実行する Transact-SQL ステートメントを作成するためにタスクが費やす時間は、タスクが更新する統計数に比例します。 多数のインデックスを含むデータベースのすべてのテーブルおよびビュー内の統計の更新、または複数のデータベース内の統計の更新を実行するようにタスクが構成されている場合、タスクが Transact-SQL ステートメントを生成するには非常に長い時間がかかることがあります。  
  
## 統計の更新タスクの構成  
 プロパティは、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから設定できます。 このタスクは、 **デザイナーの** [ツールボックス] **の** [メンテナンス プランのタスク] [!INCLUDE[ssIS](../../includes/ssis-md.md)] に表示されます。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。  
  
-   [[統計の更新タスク] (メンテナンス プラン)](../Topic/Update%20Statistics%20Task%20\(Maintenance%20Plan\).md)  
  
## 関連タスク  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。  
  
-   [タスクまたはコンテナーのプロパティを設定する](../Topic/Set%20the%20Properties%20of%20a%20Task%20or%20Container.md)  
  
## 参照  
 [Integration Services タスク](../../integration-services/control-flow/integration-services-tasks.md)   
 [制御フロー](../../integration-services/control-flow/control-flow.md)  
  
  