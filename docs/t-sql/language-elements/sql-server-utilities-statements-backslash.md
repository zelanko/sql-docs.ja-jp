---
title: "円記号 (行の連結) (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server (starting with 2008)
f1_keywords:
- '\_TSQL'
- '\'
dev_langs: TSQL
helpviewer_keywords:
- backwhack
- backslash
- excape character
- hack character
- '\ (backslash)'
- backslant
- bash
- reverse slant
- slosh
- reversed virgule
- line continuation character
- reverse solidus
ms.assetid: c97fbb20-3d12-4d0b-9b52-62a229bc83c0
caps.latest.revision: "22"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 99586a80cce43c89aa7ce9a76c84e74652d343be
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="backslash-line-continuation-transact-sql"></a>円記号 (行の連結) (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

`\`長い文字列定数、文字またはバイナリを読みやすくするための 2 つ以上の行に分割します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
<first section of string> \  
<continued section of string>  
```  
  
## <a name="arguments"></a>引数  
 \<文字列の最初のセクション >  
 文字列の先頭を指定します。  
  
 \<文字列のセクションの続き >  
 文字列の 2 行目以降を指定します。  
  
## <a name="remarks"></a>解説  
 このコマンドは、文字列の 1 行目と 2 行目以降を 1 つの文字列として、円記号を含めずに返します。  

## <a name="examples"></a>使用例  

### <a name="a-splitting-a-character-string"></a>A. 文字の文字列の分割  

次の例では、円記号と復帰を使用して、2 つの行に、文字の文字列を分割します。  
  
```  
SELECT 'abc\  
def' AS [ColumnResult];  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 ColumnResult  
 ------------  
 abcdef
 ```    

### <a name="b-splitting-a-binary-string"></a>B. バイナリ文字列の分割  

次の例では、円記号と復帰を使用して、バイナリ文字列を 2 つの行に分割します。  

```  
SELECT 0xabc\  
def AS [ColumnResult];  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 ColumnResult  
 ------------  
 0xABCDEF
 ```    

## <a name="see-also"></a>参照  
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [組み込み関数 &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [& # #40; 除算 &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/divide-transact-sql.md)   
 [& # #40; 除算代入 &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/divide-equals-transact-sql.md)   
 [複合の演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  
