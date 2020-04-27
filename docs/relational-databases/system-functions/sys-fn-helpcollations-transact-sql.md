---
title: fn_helpcollations (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_helpcollations
- fn_helpcollations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fn_helpcollations function
- collations [SQL Server], supported
- fn_helpcollations function
ms.assetid: b5082e81-1fee-4e2c-b567-5412eaee41c1
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016|| = azure-sqldw-latest ||=azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ee626b9eef8cf2f2e80217b2a3709271a227f293
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67906121"
---
# <a name="sysfn_helpcollations-transact-sql"></a>sys.fn_helpcollations (Transact-SQL)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  サポートされているすべての照合順序の一覧を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```
fn_helpcollations ()  
```  
  
## <a name="tables-returned"></a>返されるテーブル

 **fn_helpcollations**は次の情報を返します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|名前|**sysname**|標準の照合順序名。|  
|説明|**nvarchar(1000)**|照合順序の説明|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は Windows 照合順序をサポートします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、サポートされている Windows 照合順序の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]前に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]開発された、照合順序と呼ばれる限定された数 (<80) の照合順序もサポートしています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]照合順序は旧バージョンとの互換性のために引き続きサポートされていますが、新規の開発作業には使用しないでください。 Windows 照合順序について詳しくは、「[Windows 照合順序名 &#40;Transact-SQL&#41;](../../t-sql/statements/windows-collation-name-transact-sql.md)」をご覧ください。 照合順序の詳細については、「[Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)」 (照合順序と Unicode のサポート) を参照してください。  
  
## <a name="examples"></a>使用例

 次の例では、文字`L`で始まるすべての照合順序名と、バイナリ並べ替え照合順序を返します。

> [!Note]
> Fn_helpcollations () に対する Azure SQL Data Warehouse クエリは、master データベースで実行する必要があります。  
  
```sql  
SELECT Name, Description FROM fn_helpcollations()  
WHERE Name like 'L%' AND Description LIKE '% binary sort';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Name                   Description  
 -------------------    ------------------------------------  
 Lao_100_BIN            Lao-100, binary sort  
 Latin1_General_BIN     Latin1-General, binary sort  
 Latin1_General_100_BIN Latin1-General-100, binary sort  
 Latvian_BIN            Latvian, binary sort  
 Latvian_100_BIN        Latvian-100, binary sort  
 Lithuanian_BIN         Lithuanian, binary sort  
 Lithuanian_100_BIN     Lithuanian-100, binary sort  
  
 (7 row(s) affected)  
 ```
  
## <a name="see-also"></a>参照

[COLLATE &#40;Transact-SQL&#41;](~/t-sql/statements/collations.md)   
[COLLATIONPROPERTY &#40;Transact-sql&#41;](../../t-sql/functions/collation-functions-collationproperty-transact-sql.md)  
[Azure SQL Data Warehouse でのデータベースの照合順序のサポート](https://azure.microsoft.com/blog/database-collation-support-for-azure-sql-data-warehouse-2)  