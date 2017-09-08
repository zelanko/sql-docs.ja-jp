---
title: "QUOTENAME (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- QUOTENAME_TSQL
- QUOTENAME
dev_langs:
- TSQL
helpviewer_keywords:
- delimited identifiers [SQL Server]
- input strings [SQL Server]
- Unicode [SQL Server], delimited identifiers
- QUOTENAME function
- valid identifiers [SQL Server]
ms.assetid: 34d47f1e-2ac7-4890-8c9c-5f60f115e076
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7f4e40797fc49e8a70b01162fc6959ad60475e8b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="quotename-transact-sql"></a>QUOTENAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Unicode 文字列に区切り記号を追加して返すことで、入力文字列から区切り記号で囲まれた有効な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 識別子を作成します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
QUOTENAME ( 'character_string' [ , 'quote_character' ] )   
```  
  
## <a name="arguments"></a>引数  
 '*character_string*'  
 Unicode 文字データの文字列を指定します。 *character_string*は**sysname**は 128 文字に制限されます。 128 文字を超える文字を入力すると、NULL が返されます。  
  
 '*区切り記号*'  
 区切り記号として使用する 1 つの文字を指定します。 単一引用符を指定できます ( **'** )、左または右角かっこ ( **:operator[]** )、または二重引用符 ( **"** )。 場合*区切り記号*が指定されていない、角かっこを使用します。  
  
## <a name="return-types"></a>戻り値の型  
 **nvarchar (258)**  
  
## <a name="examples"></a>使用例  
 次の例は、文字の文字列`abc[]def`を使用して、`[`と`]`を作成する有効な文字[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子が区切られます。  
  
```  
SELECT QUOTENAME('abc[]def');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
[abc[]]def]  
  
(1 row(s) affected)  
```  
  
 文字列 `abc[]def` 内の右角かっこが 2 つ続いてエスケープ文字を表していることに注意してください。  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例は、文字の文字列`abc def`を使用して、`[`と`]`を作成する有効な文字[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子が区切られます。  
  
```  
SELECT QUOTENAME('abc def');   
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
[abc def]  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>参照  
 [文字列関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)  
  
  


