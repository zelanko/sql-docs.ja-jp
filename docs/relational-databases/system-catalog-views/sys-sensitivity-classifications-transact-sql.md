---
title: sys.sensitivity_classifications (TRANSACT-SQL) |Microsoft Docs
ms.date: 03/25/2019
ms.reviewer: ''
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
ms.custom: ''
ms.manager: craigg
ms.author: arib
author: vainolo
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
ms.openlocfilehash: c87f0fd65f5657d2885a2c7ea078ecaea7a2c717
ms.sourcegitcommit: 4cb96c291529e9bdf0a95fb3610b350583eb36d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65709112"
---
# <a name="syssensitivityclassifications-transact-sql"></a>sys.sensitivity_classifications (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

データベース内の各分類済みの項目の行を返します。

|列名|データ型|説明|
|-----------------|---------------|-----------------|  
|**class**|**int**|分類が存在するアイテムのクラスを識別します。|  
|**class_desc**|**varchar(16)**|分類が存在するアイテムのクラスの説明|  
|**major_id**|**int**|分類が存在する項目の ID。 < br \>< br\>クラスが 0 の場合、major_id は常に 0 です。<br>class が 1、2、または 7 の場合、major_id は object_id になります。|  
|**minor_id**|**int**|分類が存在する項目のセカンダリ ID は、そのクラスに基づいて解釈されます。<br><br>場合クラス = 1 の場合、minor_id は、column_id (場合列)、それ以外の場合 0 (場合オブジェクト)。<br>class が 2 の場合、minor_id は parameter_id になります。<br>場合クラス = 7 の場合、minor_id は index_id します。 |  
|**label**|**sysname**|秘密度の分類に割り当てられているラベル (人間が判読できる)|  
|**label_id**|**sysname**|情報の保護システムなど、Azure Information Protection (AIP) が使用できると、ラベルに関連付けられた ID|  
|**information_type**|**sysname**|秘密度の分類に割り当てられている情報の種類 (人間が判読できる)|  
|**information_type_id**|**sysname**|情報の保護システムなど、Azure Information Protection (AIP) で使用できる情報の種類に関連付けられている ID|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="remarks"></a>コメント  

- このビューは、データベースの分類状態を可視化を提供します。 データベースの分類を管理するため、およびレポートを生成するために使用できます。
- データベースの列の現在の専用の分類がサポートされています。 したがいまして：
    - **クラス**-1 (列を表す) の値は常に
    - **class_desc** -値は常に*OBJECT_OR_COLUMN*
    - **major_id** -sys.all_objects.object_id に対応する分類済みの列を含むテーブルの ID を表します。
    - **minor_id** -分類が存在する、sys.all_columns.column_id に対応する列の ID を表します。

## <a name="examples"></a>使用例

### <a name="a-listing-all-classified-columns-and-their-corresponding-classification"></a>A. 分類済みのすべての列および対応する分類の一覧

次の例で返されるテーブル名、列名、ラベルの一覧を示すテーブルはラベル ID、情報の種類、データベースの各分類済みの列の情報の種類 ID です。

> [!NOTE]
> ラベルは、Azure SQL Data Warehouse のキーワードです。

```sql
SELECT
    sys.all_objects.name AS [TableName], sys.all_columns.name As [ColumnName],
    [Label], [Label_ID], [Information_Type], [Information_Type_ID]
FROM
          sys.sensitivity_classifications
left join sys.all_objects on sys.sensitivity_classifications.major_id = sys.all_objects.object_id
left join sys.all_columns on sys.sensitivity_classifications.major_id = sys.all_columns.object_id
                         and sys.sensitivity_classifications.minor_id = sys.all_columns.column_id
```

## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  

## <a name="see-also"></a>参照  

[ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[DROP SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[SQL Information Protection の概要](https://aka.ms/sqlip)
