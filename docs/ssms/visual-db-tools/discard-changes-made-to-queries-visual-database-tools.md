---
title: "クエリに対する変更の破棄 (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reverting queries
- queries [SQL Server], discarding changes
- discarding query changes
ms.assetid: 7bb17ece-1222-4622-b476-5789d7641c64
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8b1e89b785a2f490d15594f7ecc786b40b6c9dec
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="discard-changes-made-to-queries-visual-database-tools"></a>クエリに対する変更の破棄 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] 変更を保存する前であれば、クエリ定義に対して行った変更を破棄できます。 いったん変更を保存すると、変更前の状態に戻すことはできなくなります。  
  
> [!NOTE]  
> 結果ペインで値に行った変更を元に戻すには、レコードから移動する前に Esc キーを押します。 レコードから移動して、変更がデータベースにコミットされないという通知を受け取った場合も、Esc キーを押すことで前の値に戻ることができます。  
  
### <a name="to-discard-changes-made-to-a-query-definition"></a>クエリ定義に行った変更を破棄するには  
  
1.  クエリを開いているクエリおよびビュー デザイナーで、 **[ファイル]** メニューの **[閉じる]**をクリックします。  
  
2.  **[Microsoft SQL Server Management Studio]** ダイアログ ボックスで **[いいえ]**を選択します。  
  
    クエリの定義が前回保存した状態に戻ります。  
  
## <a name="see-also"></a>参照  
[クエリの保存 (Visual Database Tools)](../../ssms/visual-db-tools/save-queries-visual-database-tools.md)  
[クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[クエリに関する基本操作の実行 (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
[結果ペインのデータの操作 (Visual Database Tools)](../../ssms/visual-db-tools/work-with-data-in-the-results-pane-visual-database-tools.md)  
  
