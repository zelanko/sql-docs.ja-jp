---
title: 検索条件の指定 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- choosing search criteria
- search conditions [SQL Server], specifying
- search criteria [SQL Server], specifying conditions
ms.assetid: 18e2c759-68ec-4efe-b208-2f73418cd9bd
author: stevestein
ms.author: sstein
ms.openlocfilehash: cfc9107b47db312778502191560ce7920c96a37b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85000843"
---
# <a name="specify-search-conditions-visual-database-tools"></a>検索条件の指定 (Visual Database Tools)
  検索条件を指定することによって、クエリで表示されるデータ行を指定できます。 たとえば、 `employee` テーブルに対してクエリを実行する場合、特定の地域で勤務している従業員だけを検索するようにクエリで指定できます。  
  
 検索条件は式で指定します。 一般に、式は演算子および検索値で構成されています。 たとえば、特定の販売地域の従業員を検索するには、 `region` 列に対して次のように検索条件を指定します。  
  
```  
='UK'  
```  
  
> [!NOTE]  
>  複数のテーブルを使用する場合、クエリおよびビュー デザイナーは各検索条件をチェックして、作成された比較が結合文になるかどうかを確認します。 比較が結合になる場合、クエリおよびビュー デザイナーは自動的に検索条件を結合に変換します。 詳細については、「[テーブルの自動結合 (Visual Database Tools)](visual-database-tools.md)」を参照してください。  
  
### <a name="to-specify-search-conditions"></a>検索条件を指定するには  
  
1.  検索条件で使用する列または式を追加していない場合は、列または式を抽出条件ペインに追加します。  
  
     選択クエリを作成し、検索列または検索式をクエリ出力に表示しない場合は、各検索列または検索式に該当する **[出力]** 列をオフにして、出力列から削除します。  
  
2.  検索するデータ列または式を含む行を見つけ、 **[フィルター]** 列に検索条件を入力します。  
  
    > [!NOTE]  
    >  演算子を入力しない場合、等値演算子 "=" が自動的に挿入されます。  
  
 クエリおよびビュー デザイナーは、WHERE 句を追加または変更して、 [SQL ペイン](sql-pane-visual-database-tools.md) の SQL ステートメントを更新します。  
  
## <a name="see-also"></a>参照  
 [Visual Database Tools &#40;検索値を入力するための規則&#41;](rules-for-entering-search-values-visual-database-tools.md)   
 [検索基準の指定 (Visual Database Tools)](specify-search-criteria-visual-database-tools.md)  
  
  
