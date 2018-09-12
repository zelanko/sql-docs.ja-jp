---
title: 重複する行の除外 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- row duplicates [SQL Server]
- duplicate rows
- row excluded in search [SQL Server]
- result sets [SQL Server], duplicate values
- excluding rows
ms.assetid: ab35a363-421d-4665-946b-ae3f6397af50
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fd83e73a0a7b94f7963531baa167669850ef0b8c
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "43807618"
---
# <a name="exclude-duplicate-rows-visual-database-tools"></a>重複する行の除外 (Visual Database Tools)
  結果セットに一意の値だけが必要な場合は、結果セットからの重複の削除を指定できます。  
  
### <a name="to-exclude-duplicate-rows-from-the-result-set"></a>結果セットから重複行を削除するには  
  
1.  ダイアグラム ペインの背景を右クリックし、ショートカット メニューの **[プロパティ]** を選択します。  
  
2.  プロパティ ウィンドウの **[一意の値]** をクリックし、値を **[はい]** に設定します。  
  
     SQL ステートメントの表示列の一覧の前にキーワード DISTINCT が挿入されます。  
  
    > [!NOTE]  
    >  DISTINCT キーワードを使用する場合、結果ペインで結果セットを変更できない場合があります。  
  
## <a name="see-also"></a>参照  
 [検索条件を指定&#40;Visual Database Tools&#41;](visual-database-tools.md)   
 [クエリ結果の並べ替えおよびグループ化 (Visual Database Tools)](sort-and-group-query-results-visual-database-tools.md)  
  
  
