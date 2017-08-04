---
title: "インデックスの再構成タスク |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.reorganizeindextask.f1
helpviewer_keywords:
- reorganizing indexes
- Reorganize Index task [Integration Services]
- indexes [Integration Services]
ms.assetid: 9ed87861-e5c3-4fcd-8760-d112f4c0af0c
caps.latest.revision: 43
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6b9cdd0be56414ccc4e80b4657bd33045b8ad931
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="reorganize-index-task"></a>インデックスの再編成タスク
  インデックスの再編成タスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのテーブルおよびビューのインデックスを再編成します。 インデックスの管理の詳細については、「 [インデックスの再編成と再構築](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)」を参照してください。  
  
 インデックスの再編成タスクを使用すると、パッケージは単一データベースまたは複数データベースのインデックスを再編成できます。 タスクにより単一データベースのインデックスのみを再編成する場合、インデックスの再編成の対象となるビューまたはテーブルを選択できます。 また、インデックスの再編成タスクには、ラージ オブジェクト データを圧縮するオプションが含まれます。 ラージ オブジェクト データとは、**image**、**text**、**ntext**、**varchar(max)**、**nvarchar(max)**、**varbinary(max)**、または **xml** データ型のデータのことです。 詳細については、「[データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)」を参照してください。  
  
 インデックスの再編成タスクは、Transact-SQL ALTER INDEX ステートメントをカプセル化します。 ラージ オブジェクト データの圧縮を選択した場合、Transact-SQL ALTER INDEX ステートメントは REORGANIZE WITH (LOB_COMPACTION = ON) 句を使用します。それ以外の場合は、LOB_COMPACTION が OFF に設定されます。 詳細については、「[ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)」を参照してください。  
  
> [!IMPORTANT]  
>  実行する Transact-SQL ステートメントを作成するためにタスクが費やす時間は、タスクが再編成するインデックス数に比例します。 多数のインデックスを含むデータベースのすべてのテーブルおよびビュー内のインデックスの再編成、または複数のデータベース内のインデックスの再編成を実行するようにタスクが構成されている場合、タスクが Transact-SQL ステートメントを生成するには非常に長い時間がかかることがあります。  
  
## <a name="configuration-of-the-reorganize-index-task"></a>インデックスの再構成タスクの構成  
 プロパティは、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから設定できます。 このタスクは、 **デザイナーの** [ツールボックス] **の** [メンテナンス プランのタスク] [!INCLUDE[ssIS](../../includes/ssis-md.md)] に表示されます。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。  
  
-   [[インデックスの再構成タスク] &#40;メンテナンス プラン&#41;](../../relational-databases/maintenance-plans/reorganize-index-task-maintenance-plan.md)  
  
## <a name="related-tasks"></a>関連タスク  
 これらのプロパティを [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定する方法の詳細については、「 [タスクまたはコンテナーのプロパティを設定する](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Integration Services タスク](../../integration-services/control-flow/integration-services-tasks.md)   
 [制御フロー](../../integration-services/control-flow/control-flow.md)  
  
  
