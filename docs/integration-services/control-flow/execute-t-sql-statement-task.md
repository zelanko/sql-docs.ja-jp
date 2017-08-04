---
title: "T-SQL ステートメントの実行タスクを実行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.executetsqlstatementtask.f1
helpviewer_keywords:
- Transact-SQL statements, SSIS
- statements [Integration Services]
- Execute T-SQL Statement task [Integration Services]
ms.assetid: 7e9086ca-d27e-46c0-bfad-d61333ebd55e
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 94fd411504f1781041e8d36f3f1cf41f6082aa09
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="execute-t-sql-statement-task"></a>T-SQL ステートメントの実行タスク
  T-SQL ステートメントの実行タスクは、Transact-SQL ステートメントを実行します。 詳細については、「[Transact-SQL リファレンス (データベース エンジン)](../../t-sql/transact-sql-reference-database-engine.md)」および「[Integration Services (SSIS) のクエリ](../../integration-services/integration-services-ssis-queries.md)」を参照してください。  
  
 このタスクは、SQL 実行タスクと同様です。 ただし、T-SQL ステートメントの実行タスクでは、SQL 言語の Transact-SQL バージョンのみがサポートされるため、このタスクを使用して、SQL 言語の他の仕様の言語によるステートメントをサーバーで実行することはできません。 パラメーター化クエリの実行、クエリ結果の変数への保存、またはプロパティ式の使用が必要な場合は、T-SQL ステートメントの実行タスクではなく、SQL 実行タスクを使用する必要があります。 詳細については、「 [SQL 実行タスク](../../integration-services/control-flow/execute-sql-task.md)」を参照してください。  
  
## <a name="configuration-of-the-execute-t-sql-task"></a>T-SQL 実行タスクの構成  
 プロパティは、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから設定できます。 このタスクは、 **デザイナーの** [ツールボックス] **の** [メンテナンス プランのタスク] [!INCLUDE[ssIS](../../includes/ssis-md.md)] に表示されます。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。  
  
-   [[T-SQL ステートメントの実行タスク] (メンテナンス プラン)](../../relational-databases/maintenance-plans/execute-t-sql-statement-task-maintenance-plan.md)  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。  
  
-   [タスクまたはコンテナーのプロパティを設定する](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
## <a name="see-also"></a>参照  
 [Integration Services タスク](../../integration-services/control-flow/integration-services-tasks.md)   
 [制御フロー](../../integration-services/control-flow/control-flow.md)   
 [Integration services パッケージをマージします。](../../integration-services/control-flow/merge-in-integration-services-packages.md)  
  
  
