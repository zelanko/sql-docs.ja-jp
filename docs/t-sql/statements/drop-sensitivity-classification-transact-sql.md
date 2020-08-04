---
title: DROP SENSITIVITY CLASSIFICATION (Transact-SQL) | Microsoft Docs
ms.date: 03/25/2019
ms.reviewer: ''
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
ms.custom: ''
ms.author: giladm
author: giladmit
f1_keywords:
- DROP SENSITIVITY CLASSIFICATION
- DROP_SENSITIVITY_CLASSIFICATION
dev_langs:
- TSQL
helpviewer_keywords:
- DROP SENSITIVITY CLASSIFICATION statement
- dropping labels
- drop labels
- removing labels
- remove labels
- classification [SQL]
- labels [SQL]
- information types
- data classification
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: d70e4a10601ab7c9171ddccf41a9ab9e5b2395c7
ms.sourcegitcommit: bc10ec0be5ddfc5f0bc220a9ac36c77dd6b80f1d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/03/2020
ms.locfileid: "87544321"
---
# <a name="drop-sensitivity-classification-transact-sql"></a>DROP SENSITIVITY CLASSIFICATION (Transact-SQL)
[!INCLUDE [asdb-asdbmi-asa](../../includes/applies-to-version/asdb-asdbmi-asa.md)]

1 つ以上のデータベース列から秘密度の分類に関するメタデータを削除します。

## <a name="syntax"></a>構文

```syntaxsql
DROP SENSITIVITY CLASSIFICATION FROM
    <object_name> [, ...n ]

<object_name> ::=
{
    [schema_name.]table_name.column_name
}
```  

## <a name="arguments"></a>引数  

*object_name* ([schema_name.]table_name.column_name)

分類を削除するデータベース列の名前です。 現在サポートされているのは列の分類のみです。
    - *schema_name* (省略可能) - 分類される列が属するスキーマの名前です。
    - *table_name* - 分類される列が属するテーブルの名前です。
    - *column_name* - 分類を削除する列の名前です。

## <a name="remarks"></a>解説  

- 1 つの "DROP SENSITIVITY CLASSIFICATION" ステートメントを使用して複数のオブジェクトの分類を削除できます。

## <a name="permissions"></a>アクセス許可  

ALTER ANY SENSITIVITY CLASSIFICATION 権限が必要です。 ALTER ANY SENSITIVITY CLASSIFICATION は、データベース権限 ALTER またはサーバー権限 CONTROL SERVER によって示されます。


## <a name="examples"></a>例  


### <a name="a-dropping-classification-from-a-single-column"></a>A. 1 つの列からの分類の削除

次の例では、`dbo.sales.price` 列から分類を削除します。  

```sql
DROP SENSITIVITY CLASSIFICATION FROM
    dbo.sales.price
```

### <a name="b-dropping-classification-from-multiple-columns"></a>B. 複数の列からの分類の削除

次の例では、`dbo.sales.price`、`dbo.sales.discount`、および `SalesLT.Customer.Phone` の各列から分類を削除します。  

```sql
DROP SENSITIVITY CLASSIFICATION FROM
    dbo.sales.price, dbo.sales.discount, SalesLT.Customer.Phone  
```

## <a name="see-also"></a>参照  

[ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[sys.sensitivity_classifications (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sensitivity-classifications-transact-sql.md)

[SQL Information Protection の概要](https://aka.ms/sqlip)
