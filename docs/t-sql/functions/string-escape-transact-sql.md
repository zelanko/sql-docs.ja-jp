---
title: "STRING_ESCAPE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/25/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STRING_ESCAPE
- STRING_ESCAPE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STRING_ESCAPE function
ms.assetid: 2163bc7a-3816-4304-9c40-8954804f5465
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 41f969e292eff76c9a836ccd3177519d88e355ac
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stringescape-transact-sql"></a>STRING_ESCAPE (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  テキストに特殊文字をエスケープし、エスケープ文字でテキストを返します。 **STRING_ESCAPE**決定的関数です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
STRING_ESCAPE( text , type )  
```  
  
## <a name="arguments"></a>引数  
 *text*  
 **Nvarchar**[式](../../t-sql/language-elements/expressions-transact-sql.md)エスケープする必要があるオブジェクトを表す式。  
  
 *型*  
 適用される規則をエスケープします。 現在サポートされている値は`'json'`します。  
  
## <a name="return-types"></a>戻り値の型  
 **nvarchar (max)**特殊のエスケープと制御文字を含むテキスト。 現在**STRING_ESCAPE**次の表に示すように JSON の特殊文字をエスケープのみです。  
  
|特殊文字|エンコードされたシーケンス|  
|-----------------------|----------------------|  
|引用符 (")|\\"|  
|逆斜線 (\\)|\\\|  
|斜線 (/)|\\/|  
|バックスペース|\b|  
|改ページ|\f|  
|改行|\n|  
|キャリッジ リターン|\r|  
|水平タブ|\t|  
  
|制御文字|エンコードされたシーケンス|  
|-----------------------|----------------------|  
|CHAR(0)|\u0000|  
|CHAR(1)|\u0001|  
|[...]|[...]|  
|CHAR(31)|\u001f|  
  
## <a name="remarks"></a>解説  
  
## <a name="examples"></a>使用例  
  
### <a name="a--escape-text-according-to-the-json-formatting-rules"></a>A.  JSON 形式の規則に従って文字列をエスケープします。  
 次のクエリでは、JSON の規則を使用して、特殊文字をエスケープし、エスケープされたテキストを返します。  
  
```  
SELECT STRING_ESCAPE('\   /  
\\    "     ', 'json') AS escapedText;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
escapedText  
-------------------------------------------------------------  
\\\t\/\n\\\\\t\"\t
```  
  
### <a name="b-format-json-object"></a>B. JSON オブジェクトの書式設定  
 次のクエリでは、数値と文字列の変数から JSON テキストを作成し、変数内の任意の特殊な JSON 文字をエスケープします。  
  
```  
SET @json = FORMATMESSAGE('{ "id": %d,"name": "%s", "surname": "%s" }',   
    17, STRING_ESCAPE(@name,'json'), STRING_ESCAPE(@surname,'json') );  
```  
  
## <a name="see-also"></a>参照  
 [文字列関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/string-functions-transact-sql.md)   
 [部分文字列と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/substring-transact-sql.md)  
  
  

