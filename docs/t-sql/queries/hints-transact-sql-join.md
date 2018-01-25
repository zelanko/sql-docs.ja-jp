---
title: "結合ヒント (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Join Hint
- Join_Hint_TSQL
dev_langs: TSQL
helpviewer_keywords:
- HASH join hint
- REMOTE join hint
- LOOP join hint
- join hints
- MERGE join hint
- hints [SQL Server], join
ms.assetid: 09069f4a-f2e3-4717-80e1-c0110058efc4
caps.latest.revision: "30"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 84f00c9acef803cd84be1c2be2fadf417d3b9bff
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="hints-transact-sql---join"></a>ヒント (TRANSACT-SQL) の参加します。
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  結合ヒントにより、クエリ オプティマイザーで、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の 2 つのテーブル間の結合方法を設定します。 結合および結合の構文の詳細については、次を参照してください。 [FROM &#40;です。TRANSACT-SQL と #41 です](../../t-sql/queries/from-transact-sql.md)。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]通常、クエリ オプティマイザーがクエリの最適な実行プランを選択、ヒントを含むことをお勧め\<join_hint >、経験を積んだ開発者、最後の手段としてのみ使用して、データベース管理者です。
  
 **適用対象:**  
  
 [DELETE](../../t-sql/statements/delete-transact-sql.md)  
  
 [SELECT](../../t-sql/queries/select-transact-sql.md)  
  
 [UPDATE](../../t-sql/queries/update-transact-sql.md)  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
<join_hint> ::=   
     { LOOP | HASH | MERGE | REMOTE }  
```  
  
## <a name="arguments"></a>引数  
 LOOP | HASH | MERGE  
 クエリ内の結合は、ループ、ハッシュ、またはマージを使用します。 LOOP | HASH | MERGE JOIN を使用すると、2 つのテーブル間に特定の結合が設定されます。 LOOP は、RIGHT または FULL と共に結合の種類として指定することはできません。  
  
 REMOTE  
 右側のテーブルのサイトで結合操作を実行します。 これは、左側のテーブルがローカル テーブルで、右側のテーブルがリモート テーブルの場合に効果的です。 REMOTE は、左側のテーブルの行数が右側のテーブルの行数よりも少ないときだけ使用します。  
  
 右側のテーブルがローカルの場合、結合はローカルで実行されます。 両方のテーブルがリモート テーブルでデータ ソースは異なる場合、REMOTE の指定によって結合は右側のテーブルのサイトで実行されます。 両方のテーブルが同じデータ ソースのリモート テーブルの場合、REMOTE は必要ありません。  
  
 結合述語で比較されている値のいずれかを COLLATE 句を使用して別の照合順序にキャストする場合は、REMOTE を使用できません。  
  
 REMOTE は、INNER JOIN 操作に対してのみ使用できます。  
  
## <a name="remarks"></a>解説  
 結合ヒントは、クエリの FROM 句で指定します。 結合ヒントにより、2 つのテーブル間の結合方法を設定できます。 2 つのテーブルに対して結合ヒントが指定されると、クエリ オプティマイザーは、ON キーワードの位置に基づいて、クエリ内のすべての結合テーブルに対して結合の順番を自動的に設定します。 ON 句を指定せずに CROSS JOIN を使用する場合は、かっこを使用して結合の順番を指定できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-hash"></a>A. HASH を使用する  
 次の例を指定する、`JOIN`によってクエリ内の操作を実行、`HASH`結合します。 この例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
SELECT p.Name, pr.ProductReviewID  
FROM Production.Product AS p  
LEFT OUTER HASH JOIN Production.ProductReview AS pr  
ON p.ProductID = pr.ProductID  
ORDER BY ProductReviewID DESC;  
```  
  
### <a name="b-using-loop"></a>B. LOOP を使用する  
 次の例を指定する、`JOIN`によってクエリ内の操作を実行、`LOOP`結合します。 この例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
DELETE FROM Sales.SalesPersonQuotaHistory   
FROM Sales.SalesPersonQuotaHistory AS spqh  
    INNER LOOP JOIN Sales.SalesPerson AS sp  
    ON spqh.SalesPersonID = sp.SalesPersonID  
WHERE sp.SalesYTD > 2500000.00;  
GO  
```  
  
### <a name="c-using-merge"></a>C. MERGE を使用する  
 次の例を指定する、`JOIN`によってクエリ内の操作を実行、`MERGE`結合します。 この例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
SELECT poh.PurchaseOrderID, poh.OrderDate, pod.ProductID, pod.DueDate, poh.VendorID   
FROM Purchasing.PurchaseOrderHeader AS poh  
INNER MERGE JOIN Purchasing.PurchaseOrderDetail AS pod   
    ON poh.PurchaseOrderID = pod.PurchaseOrderID;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ヒント &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/hints-transact-sql.md)  
  
  
