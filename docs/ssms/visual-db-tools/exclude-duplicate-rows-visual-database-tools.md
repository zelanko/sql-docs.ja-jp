---
title: 重複する行の除外
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- row duplicates [SQL Server]
- duplicate rows
- row excluded in search [SQL Server]
- result sets [SQL Server], duplicate values
- excluding rows
ms.assetid: ab35a363-421d-4665-946b-ae3f6397af50
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 2f652c40278a44d4bbe068a441e08ffe610af002
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86012166"
---
# <a name="exclude-duplicate-rows-visual-database-tools"></a>重複する行の除外 (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
結果セットに一意の値だけが必要な場合は、結果セットからの重複の削除を指定できます。  
  
### <a name="to-exclude-duplicate-rows-from-the-result-set"></a>結果セットから重複行を削除するには  
  
1.  ダイアグラム ペインの背景を右クリックし、ショートカット メニューの **[プロパティ]** を選択します。  
  
2.  プロパティ ウィンドウの **[一意の値]** をクリックし、値を **[はい]** に設定します。  
  
    SQL ステートメントの表示列の一覧の前にキーワード DISTINCT が挿入されます。  
  
    > [!NOTE]  
    > DISTINCT キーワードを使用する場合、結果ペインで結果セットを変更できない場合があります。  
  
## <a name="see-also"></a>参照  
[検索基準の指定 (Visual Database Tools)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[クエリ結果の並べ替えおよびグループ化 (Visual Database Tools)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
  
