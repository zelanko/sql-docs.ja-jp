---
title: 値の一致しない行を選択する方法 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search conditions [SQL Server], rows not matching value
- row not matching value [SQL Server]
- NOT operator [Visual Database Tools]
- search criteria [SQL Server], rows not matching value
ms.assetid: 19898578-7b2f-401c-bb8f-9f2a017efdf7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f84f4fcc8a6dde7dcf9f556a72c2599356e231f7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63067538"
---
# <a name="select-rows-that-do-not-match-a-value-visual-database-tools"></a>値の一致しない行を選択する方法 (Visual Database Tools)
  値の一致しない行を検索するには、NOT 演算子を使用します。  
  
### <a name="to-find-rows-that-do-not-match-a-value"></a>値の一致しない行を検索するには  
  
1.  検索条件内で使用する列または式をまだ作成していない場合は、[抽出条件ペイン](visual-database-tools.md)に追加します。  
  
2.  検索するデータ列または式を含む行を見つけ、 **[フィルター]** グリッド列に NOT 演算子とそれに続く検索値を入力します。  
  
 たとえば、 `products` テーブルから、製品コード列の値が "A" 以外の文字で始まるすべての行を検索するには、検索条件を次のようにします。  
  
```  
NOT LIKE 'A%'  
```  
  
## <a name="see-also"></a>参照  
 [Visual Database Tools &#40;検索値を入力するための規則&#41;](rules-for-entering-search-values-visual-database-tools.md)   
 [検索基準の指定 (Visual Database Tools)](specify-search-criteria-visual-database-tools.md)  
  
  
