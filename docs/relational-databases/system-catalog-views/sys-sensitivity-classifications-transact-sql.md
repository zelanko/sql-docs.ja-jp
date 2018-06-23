---
title: sys.sensitivity_classifications (TRANSACT-SQL) |Microsoft ドキュメント
ms.date: 06/17/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: sql-database
ms.service: sql-database
ms.technology: t-sql
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.custom: ''
ms.manager: craigg
ms.author: giladm
author: giladmit
f1_keywords:
- 'sys.sensitivity_classifications '
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sensitivity_classifications statement
- dropping labels
- drop labels
- removing labels
- remove labels
- classification [SQL]
- labels [SQL]
- information types
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: d0adbbeb82c06d6a44f3a7439bcbf479d7358401
ms.sourcegitcommit: 70882926439a63ab9d812809429c63040eb9a41b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36262887"
---
# <a name="syssensitivityclassifications-transact-sql"></a>sys.sensitivity_classifications (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

データベースの各分類済みの項目の行を返します。

|列名|データ型|説明|
|-----------------|---------------|-----------------|  
|**class**|**int**|分類が存在するアイテムのクラスを識別します。|  
|**class_desc**|**varchar (16)**|分類が存在するアイテムのクラスの説明|  
|**major_id**|**int**|分類が存在する項目の ID です。 < br \>< br\>クラスが 0 の場合、major_id は常に 0 です。<br>class が 1、2、または 7 の場合、major_id は object_id になります。|  
|**minor_id**|**int**|分類が存在する項目のセカンダリ ID は、そのクラスに基づいて解釈されます。<br><br>場合クラス = 1、minor_id は、column_id (場合列)、それ以外の場合 0 (場合オブジェクト)。<br>class が 2 の場合、minor_id は parameter_id になります。<br>場合クラス = 7、minor_id は index_id です。 |  
|**label**|**sysname**|小文字の区別の分類のために割り当てられているラベル (人間が判読できる)|  
|**label_id**|**sysname**|Azure の情報保護 (AIP) などの情報保護システムが使用できるように、ラベルに関連付けられた ID|  
|**information_type**|**sysname**|小文字の区別の分類のために割り当てられている情報の種類 (人間が判読できる)|  
|**information_type_id**|**sysname**|Azure の情報保護 (AIP) などの情報保護システムで使用できる情報の種類に関連付けられている ID|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="remarks"></a>コメント  

- このビューは、データベースの分類の状態に可視性を提供します。 これは、データベースの分類を管理するためと、レポートを生成するために使用できます。
- データベースの列の現在は分類がサポートされています。 したがいまして：
    - **クラス**-1 (列を表す) の値は常が
    - **class_desc**の値は常が*OBJECT_OR_COLUMN*
    - **major_id** -sys.all_objects.object_id に対応する分類済みの列を含むテーブルの ID を表します
    - **minor_id** -分類が存在する、sys.all_columns.column_id に対応する列の ID を表します

## <a name="examples"></a>使用例

### <a name="a-listing-all-classified-columns-and-their-corresponding-classification"></a>A. 分類済みのすべての列と、対応する区分の一覧表示

次の例で返されるテーブル名、列名、ラベルの一覧を示すテーブルは、ID、情報の種類、データベース内の各分類列の情報の種類の ID をラベルです。

```sql
SELECT
    sys.all_objects.name AS TableName, sys.all_columns.name As ColumnName,
    Label, Label_ID, Information_Type, Information_Type_ID
FROM
          sys.sensitivity_classifications
left join sys.all_objects on sys.sensitivity_classifications.major_id = sys.all_objects.object_id
left join sys.all_columns on sys.sensitivity_classifications.major_id = sys.all_columns.object_id
                         and sys.sensitivity_classifications.minor_id = sys.all_columns.column_id
```

## <a name="see-also"></a>参照  

[追加の区別 CLASSIFICTION (TRANSACT-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[ドロップ感度 CLASSIFICTION (TRANSACT-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[SQL Information Protection の概要](http://aka.ms/sqlip)
