---
title: sys.fn_helpcollations (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 38
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: c6b16defc5c6ffc11fc13f59d014502ee37f8398
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysfnhelpcollations-transact-sql"></a>sys.fn_helpcollations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-pdw-md.md)]

  サポートされているすべての照合順序の一覧を返します。  
  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
fn_helpcollations ()  
```  
  
## <a name="tables-returned"></a>返されたテーブル  
 **fn_helpcollations**次の情報を返します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|名前|**sysname**|標準の照合順序名。|  
|Description|**nvarchar(1000)**|照合順序の説明。|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は Windows 照合順序をサポートします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が Windows 照合順序をサポートする前に開発された、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 照合順序と呼ばれる、限られた数 (<80) の照合順序をサポートしています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 照合順序は旧バージョンとの互換性を維持するためにサポートされていますが、新規の開発作業に使用しないでください。 Windows 照合順序について詳しくは、「[Windows 照合順序名 &#40;Transact-SQL&#41;](../../t-sql/statements/windows-collation-name-transact-sql.md)」をご覧ください。 照合順序の詳細については、次を参照してください。 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)です。  
  

## <a name="examples"></a>使用例  
 次の例は、文字で始まるすべての照合順序名を返します`L`バイナリ順の照合順序であるとします。  
  
```  
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
[COLLATIONPROPERTY &#40;TRANSACT-SQL&#41;](../../t-sql/functions/collation-functions-collationproperty-transact-sql.md)  
[Azure SQL データ ウェアハウスのデータベース照合順序のサポート](https://azure.microsoft.com/blog/database-collation-support-for-azure-sql-data-warehouse-2)  

