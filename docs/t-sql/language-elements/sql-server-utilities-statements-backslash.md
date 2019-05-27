---
title: 円記号 (行の連結) (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/09/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '\_TSQL'
- '\'
dev_langs:
- TSQL
helpviewer_keywords:
- backwhack
- backslash
- escape character
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4b03094aa0d75b2491e2635506c9a7b6563dacba
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65981687"
---
# <a name="backslash-line-continuation-transact-sql"></a>円記号 (行の連結) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

`\` は、読みやすくするために、長い文字列定数、文字、またはバイナリを複数の行に改行します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
<first section of string> \  
<continued section of string>  
```  
  
## <a name="arguments"></a>引数  
 \<文字列の最初のセクション>  
 文字列の先頭を指定します。  
  
 \<文字列の継続するセクション>  
 文字列の 2 行目以降を指定します。  
  
## <a name="remarks"></a>Remarks  
 このコマンドは、文字列の 1 行目と 2 行目以降を 1 つの文字列として、円記号を含めずに返します。  

## <a name="examples"></a>使用例  

### <a name="a-splitting-a-character-string"></a>A. 文字列を分割する  

次の例では、円記号と復帰を使用して文字列を 2 行に分けます。  
  
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

### <a name="b-splitting-a-binary-string"></a>B. バイナリ文字列を分割する  

次の例では、円記号と復帰を使用してバイナリ文字列を 2 行に分けます。  

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
 [演算子 &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [&#40;除算&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/divide-transact-sql.md)   
 [&#40;除算代入&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/divide-equals-transact-sql.md)   
 [複合演算子 &#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  
