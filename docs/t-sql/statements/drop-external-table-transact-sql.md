---
title: DROP EXTERNAL TABLE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 02a6a236-0756-4570-abfa-6f677a7df042
caps.latest.revision: 12
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f3ee582f69a0ce12c1ac0054e4be6fbff82da953
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/04/2018
ms.locfileid: "37782533"
---
# <a name="drop-external-table-transact-sql"></a>外部テーブル (TRANSACT-SQL) を削除します。
[!INCLUDE[tsql-appliesto-ss2016-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2016-xxxx-asdw-pdw-md.md)]

  PolyBase 外部テーブルを削除します。 これには、外部のデータは削除されません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DROP EXTERNAL TABLE [ database_name . [schema_name ] . | schema_name . ] table_name   
[;]  
```  
  

## <a name="arguments"></a>引数  
 [ *database_name* . [*schema_name*] . | *schema_name* . ] *table_name*  
 削除する外部テーブルの 1 つか 3 部構成の名前。 テーブル名は、スキーマ、または、データベースとスキーマ オプションで含めることができます。  
  
## <a name="permissions"></a>アクセス許可  
  
-   テーブルが属するスキーマに対する **ALTER** 権限が必要です。  
  
## <a name="general-remarks"></a>全般的な解説  
 外部のテーブルを削除するには、すべてのテーブルに関連するメタデータを削除します。 外部のデータは削除されません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-basic-syntax"></a>A. 基本的な構文を使用します。  
  
```  
DROP EXTERNAL TABLE SalesPerson;  
DROP EXTERNAL TABLE dbo.SalesPerson;  
DROP EXTERNAL TABLE EasternDivision.dbo.SalesPerson;  
```  
  
### <a name="b-dropping-an-external-table-from-the-current-database"></a>B. 現在のデータベースから、外部テーブルを削除します。  
 次の例では、現在のデータベースから、`ProductVendor1` テーブル、そのデータ、インデックス、およびすべての依存ビューを削除します。  
  
```  
DROP EXTERNAL TABLE ProductVendor1;  
```  
  
### <a name="c-dropping-a-table-from-another-database"></a>C. 別のデータベースからテーブルを削除します。  
 次の例では、`EasternDivision` データベースにある `SalesPerson` テーブルを削除します。  
  
```  
DROP EXTERNAL TABLE EasternDivision.dbo.SalesPerson;  
```  
  
## <a name="see-also"></a>参照  
 [CREATE EXTERNAL TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-external-table-transact-sql.md)  
  
  

