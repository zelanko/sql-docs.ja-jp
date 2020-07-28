---
title: 検索条件の指定
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- choosing search criteria
- search conditions [SQL Server], specifying
- search criteria [SQL Server], specifying conditions
ms.assetid: 18e2c759-68ec-4efe-b208-2f73418cd9bd
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: e1541a4602c53c96dfad36c549bc75c8cf76fae5
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "85999265"
---
# <a name="specify-search-conditions-visual-database-tools"></a>検索条件の指定 (Visual Database Tools)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
検索条件を指定することによって、クエリで表示されるデータ行を指定できます。 たとえば、 `employee` テーブルに対してクエリを実行する場合、特定の地域で勤務している従業員だけを検索するようにクエリで指定できます。  
  
検索条件は式で指定します。 一般に、式は演算子および検索値で構成されています。 たとえば、特定の販売地域の従業員を検索するには、 `region` 列に対して次のように検索条件を指定します。  
  
```  
='UK'  
```  
  
> [!NOTE]  
> 複数のテーブルを使用する場合、クエリおよびビュー デザイナーは各検索条件をチェックして、作成された比較が結合文になるかどうかを確認します。 比較が結合になる場合、クエリおよびビュー デザイナーは自動的に検索条件を結合に変換します。 詳細については、「[テーブルの自動結合 (Visual Database Tools)](../../ssms/visual-db-tools/join-tables-automatically-visual-database-tools.md)」を参照してください。  
  
### <a name="to-specify-search-conditions"></a>検索条件を指定するには  
  
1.  検索条件で使用する列または式を追加していない場合は、列または式を抽出条件ペインに追加します。  
  
    選択クエリを作成し、検索列または検索式をクエリ出力に表示しない場合は、各検索列または検索式に該当する **[出力]** 列をオフにして、出力列から削除します。  
  
2.  検索するデータ列または式を含む行を見つけ、 **[フィルター]** 列に検索条件を入力します。  
  
    > [!NOTE]  
    > 演算子を入力しない場合、等値演算子 "=" が自動的に挿入されます。  
  
クエリおよびビュー デザイナーは、WHERE 句を追加または変更して、 [SQL ペイン](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md) の SQL ステートメントを更新します。  
  
## <a name="see-also"></a>参照  
[検索値を入力するときの規則 (Visual Database Tools)](../../ssms/visual-db-tools/rules-for-entering-search-values-visual-database-tools.md)  
[検索基準の指定 (Visual Database Tools)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
  
