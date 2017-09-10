---
title: "@@LANGUAGE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@LANGUAGE_TSQL'
- '@@LANGUAGE'
dev_langs:
- TSQL
helpviewer_keywords:
- languages [SQL Server], current in use
- '@@LANGUAGE function'
- current language in use
- names [SQL Server], language in use
ms.assetid: 3e13b477-7dfa-4da6-9948-da2050d42527
caps.latest.revision: 21
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7cbf02aa47a4623d78062a63aa2c159f63ddd47e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="language-transact-sql"></a>@@LANGUAGE (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在使用されている言語の名前を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
@@LANGUAGE  
```  
  
## <a name="return-types"></a>戻り値の型  
 **nvarchar**  
  
## <a name="remarks"></a>解説  
 有効な公式言語名を含めて、言語設定に関する情報を表示するには実行**sp_helplanguage**パラメーターを指定します。  
  
## <a name="examples"></a>使用例  
 次の例では、現在のセッションで使用されている言語を返します。  
  
```  
SELECT @@LANGUAGE AS 'Language Name';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Language Name                   
------------------------------  
us_english                      
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、現在のセッションで使用されている言語を返します。  
  
```  
SELECT @@LANGUAGE AS 'Language Name';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Language Name                   
------------------------------  
us_english                      
```  
  
## <a name="see-also"></a>参照  
 [構成関数 &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [言語を設定する & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-language-transact-sql.md)   
 [sp_helplanguage & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helplanguage-transact-sql.md)  
  
  


