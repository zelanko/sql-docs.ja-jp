---
title: sensitivity_classifications (Transact-sql) |Microsoft Docs
ms.date: 03/25/2019
ms.reviewer: ''
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
ms.custom: ''
ms.author: mibar
author: barmichal
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
ms.openlocfilehash: a9d14cd93b08c0094ad984a6469b433e0b266479
ms.sourcegitcommit: 77293fb1f303ccfd236db9c9041d2fb2f64bce42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929779"
---
# <a name="syssensitivity_classifications-transact-sql"></a>sensitivity_classifications (Transact-sql)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

データベース内の分類されたアイテムごとに1行のデータを返します。

|列名|データ型|説明|
|-----------------|---------------|-----------------|  
|**class**|**int**|分類が存在する項目のクラスを識別します。|  
|**class_desc**|**varchar (16)**|分類が存在する項目のクラスの説明|  
|**major_id**|**int**|分類が存在する項目の ID。 < br \>< br \>の場合、クラスが0の場合、major_id は常に0です。<br>class が 1、2、または 7 の場合、major_id は object_id になります。|  
|**minor_id**|**int**|分類が存在する項目のセカンダリ ID。クラスに従って解釈されます。<br><br>Class が1の場合、minor_id は column_id (if 列)、それ以外の場合は 0 (if object) です。<br>class が 2 の場合、minor_id は parameter_id になります。<br>Class が7の場合、minor_id は index_id です。 |  
|**label**|**sysname**|秘密度の分類に割り当てられたラベル (人間が判読可能)|  
|**label_id**|**sysname**|ラベルに関連付けられた ID。 Azure Information Protection (AIP) などの情報保護システムで使用できます。|  
|**information_type**|**sysname**|秘密度の分類に割り当てられた情報の種類 (人間が判読可能)|  
|**information_type_id**|**sysname**|情報の種類に関連付けられた ID。 Azure Information Protection (AIP) などの情報保護システムで使用できます。|  
| &nbsp; | &nbsp; | &nbsp; |

## <a name="remarks"></a>コメント  

- このビューでは、データベースの分類状態を表示できます。 データベースの分類を管理したり、レポートを生成したりするために使用できます。
- 現在、データベース列の分類のみがサポートされています。 したがいまして：
    - **クラス**-常に値 1 (列を表す) を持つ
    - **class_desc** -常に値*OBJECT_OR_COLUMN*が設定されます。
    - **major_id** -分類された列を含むテーブルの id を表します。この id は、sys. all オブジェクト. object_id に相当します。
    - **minor_id** -分類が存在する列の id を表します。これは、column_id に対応します。

## <a name="examples"></a>使用例

### <a name="a-listing-all-classified-columns-and-their-corresponding-classification"></a>A. 分類されたすべての列とそれに対応する分類の一覧表示

次の例では、データベース内の分類された各列のテーブル名、列名、ラベル、ラベル ID、情報の種類、情報の種類の ID を一覧表示しています。

> [!NOTE]
> Label は Azure SQL Data Warehouse のキーワードです。

```sql
SELECT
    SCHEMA_NAME(sys.all_objects.schema_id) as SchemaName,
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

## <a name="see-also"></a>関連項目  

[ADD SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/add-sensitivity-classification-transact-sql.md)

[DROP SENSITIVITY CLASSIFICATION (Transact-SQL)](../../t-sql/statements/drop-sensitivity-classification-transact-sql.md)

[SQL Information Protection の概要](https://aka.ms/sqlip)
