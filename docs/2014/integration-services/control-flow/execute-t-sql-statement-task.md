---
title: T-SQL ステートメントの実行タスク | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executetsqlstatementtask.f1
helpviewer_keywords:
- Transact-SQL statements, SSIS
- statements [Integration Services]
- Execute T-SQL Statement task [Integration Services]
ms.assetid: 7e9086ca-d27e-46c0-bfad-d61333ebd55e
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 36aac75b9fece324fd2ee9f8f31dff43b549ee3a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37281688"
---
# <a name="execute-t-sql-statement-task"></a>T-SQL ステートメントの実行タスク
  T-SQL ステートメントの実行タスクは、Transact-SQL ステートメントを実行します。 詳細については、「[Transact-SQL リファレンス (データベース エンジン)](/sql/t-sql/language-reference)」および「[Integration Services (SSIS) のクエリ](../integration-services-ssis-queries.md)」を参照してください。  
  
 このタスクは、SQL 実行タスクと同様です。 ただし、T-SQL ステートメントの実行タスクでは、SQL 言語の Transact-SQL バージョンのみがサポートされるため、このタスクを使用して、SQL 言語の他の仕様の言語によるステートメントをサーバーで実行することはできません。 パラメーター化クエリの実行、クエリ結果の変数への保存、またはプロパティ式の使用が必要な場合は、T-SQL ステートメントの実行タスクではなく、SQL 実行タスクを使用する必要があります。 詳細については、「 [SQL 実行タスク](execute-sql-task.md)」を参照してください。  
  
## <a name="configuration-of-the-execute-t-sql-task"></a>T-SQL 実行タスクの構成  
 プロパティは、 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから設定できます。 このタスクは、 **デザイナーの** [ツールボックス] **の** [メンテナンス プランのタスク] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] に表示されます。  
  
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。  
  
-   [[T-SQL ステートメントの実行タスク] (メンテナンス プラン)](../../relational-databases/maintenance-plans/execute-t-sql-statement-task-maintenance-plan.md)  
  
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックを参照してください。  
  
-   [タスクまたはコンテナーのプロパティを設定する](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a>参照  
 [Integration Services タスク](integration-services-tasks.md)   
 [制御フロー](control-flow.md)   
 [Integration Services パッケージで MERGE を実行する](merge-in-integration-services-packages.md)  
  
  
