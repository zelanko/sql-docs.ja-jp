---
title: "COLLATIONPROPERTY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COLLATIONPROPERTY_TSQL
- COLLATIONPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- collations [SQL Server], properties
- COLLATIONPROPERTY function
ms.assetid: f5029e74-a1db-4f69-b0f5-5ee920c3311d
caps.latest.revision: 44
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 94cbf96a25a84af1eddce9d94555be9c558c3470
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="collation-functions---collationproperty-transact-sql"></a>照合順序関数、COLLATIONPROPERTY (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

指定された照合順序のプロパティを返します[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
COLLATIONPROPERTY( collation_name , property )  
```  
  
## <a name="arguments"></a>引数  
*collation_name*  
照合順序の名前を指定します。 *collation_name*は**nvarchar (128)**、既定値はありません。
  
*プロパティ*  
照合順序のプロパティを指定します。 *プロパティ*は**varchar (128)**、次の値のいずれかを指定できます。
  
|プロパティ名|Description|  
|---|---|
|**CodePage**|照合順序の Unicode 以外のコード ページ。|  
|**LCID**|照合順序の Windows LCID。|  
|**ComparisonStyle**|照合順序の Windows 比較形式。 すべてのバイナリ照合順序は、0 を返します。|  
|**バージョン**|照合順序 ID のバージョン フィールドから継承した照合順序のバージョン。 2、1、または 0 が返されます。<br /><br /> 名前に「100」との照合順序) では、2 を返します。<br /><br /> 名前に "90" が含まれる照合順序では、1 が返されます。<br /><br /> 他のすべての照合順序では 0 が返されます。|  
  
## <a name="return-types"></a>戻り値の型
**sql_variant**
  
## <a name="examples"></a>使用例  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]そして[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage')  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
## <a name="see-also"></a>参照
[sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)
  
  


