---
title: "データベースの圧縮タスク | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: control-flow
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.dts.designer.shrinkdatabasetask.f1
helpviewer_keywords:
- Shrink Database task
- database shrinking [Integration Services]
- shrinking databases
ms.assetid: e66286f8-97b1-4e5a-86b4-e56f1932b7d5
caps.latest.revision: "42"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0ccffff02bdf7bfd7369ba9d624a19c7c98906f7
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="shrink-database-task"></a>データベースの圧縮タスク
  データベースの圧縮タスクは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのデータおよびログ ファイルのサイズを縮小します。  
  
 データベースの圧縮タスクを使用すると、パッケージは単一データベースまたは複数データベースのファイルを圧縮できます。  
  
 ファイルの末尾にあるデータのページを、ファイルの先頭に近い占有されていない領域に移動することにより、データ ファイルが圧縮され、領域が回復されます。 ファイル末尾に十分な空き領域が作成された場合は、ファイル末尾のデータ ページの割り当てを解除して、ファイル システムに戻すことができます。  
  
> [!WARNING]  
>  ファイルを圧縮するために移動されたデータは、ファイル内のあらゆる使用可能な場所に分散される場合があります。 これにより、インデックスの断片化が発生し、広範なインデックスを検索するクエリのパフォーマンスが低下する場合があります。 断片化を解消するには、圧縮後にファイルのインデックスを再構築することを検討してください。  
  
## <a name="commands"></a>コマンド  
 データベースの圧縮タスクは DBCC SHRINKDATABASE コマンドをカプセル化します。DBCC SHRINKDATABASE コマンドには、次の引数とオプションが含まれます。  
  
-   *database_name*  
  
-   *target_percent*  
  
-   NOTRUNCATE または TRUNCATEONLY  
  
 データベースの圧縮タスクで複数のデータベースを圧縮する場合、複数の SHRINKDATABASE コマンドが、1 つのデータベースにつき 1 回ずつ実行されます。 SHRINKDATABASE コマンドのすべてのインスタンスは、*database_name* 引数以外の引数に同じ値を使用します。 詳細については、「[DBCC SHRINKDATABASE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md)」を参照してください。  
  
## <a name="configuration-of-the-shrink-database-task"></a>データベースの圧縮タスクの構成  
 プロパティは、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから設定できます。 このタスクは、 **デザイナーの** [ツールボックス] **の** [メンテナンス プランのタスク] [!INCLUDE[ssIS](../../includes/ssis-md.md)] に表示されます。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックを参照してください。  
  
-   [[データベースの圧縮タスク] &#40;メンテナンス プラン&#41;](../../relational-databases/maintenance-plans/shrink-database-task-maintenance-plan.md)  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでこれらのプロパティを設定する方法については、次のトピックをクリックしてください。  
  
-   [タスクまたはコンテナーのプロパティを設定する](http://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
  
