---
title: "(円記号)(TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server (starting with 2008)
f1_keywords:
- '\_TSQL'
- '\'
dev_langs:
- TSQL
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
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 011025d20b6341b9fa43b25f6c14c91a135a6ffa
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="sql-server-utilities-statements---backslash"></a>SQL Server ユーティリティのステートメントの円記号
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コマンドがない[!INCLUDE[tsql](../../includes/tsql-md.md)]によって認識される、ステートメントが、 **sqlcmd**と**osql**ユーティリティおよび[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]コード エディター。 これらのコマンドを使用すると、バッチおよびスクリプトの読み取りと実行が容易になります。  
  
\ 読みやすくするための 2 つ以上の行に長い文字列定数を分割します。  
  
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
  
 円記号がありませんが、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。 によって認識されるコマンドです、 **sqlcmd**と**osql**ユーティリティおよび[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]コード エディター。  
  
## <a name="examples"></a>使用例  
 次の例では、円記号と復帰を使用して文字列を 2 行に分けます。  
  
```  
SELECT 'abc\  
def' AS ColumnResult;  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 ColumnResult  
 ------------  
 abcdef
 ```    
  
## <a name="see-also"></a>参照  
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [組み込み関数 &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [演算子 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [& # #40; 除算 &#41;& #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/divide-transact-sql.md)   
 [&#40; 分割等号"&"#41;& #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/divide-equals-transact-sql.md)   
 [複合の演算子 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  

