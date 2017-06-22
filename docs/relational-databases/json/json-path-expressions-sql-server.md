---
title: "JSON パス式 (SQL Server) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 01/23/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JSON, path expressions
- path expressions (JSON)
ms.assetid: 25ea679c-84cc-4977-867c-2cbe9d192553
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: 44bfd54aa494dd52174eeed8479e14a99d810af3
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="json-path-expressions-sql-server"></a>JSON パス式 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 JSON オブジェクトのプロパティを参照するのにには、JSON パス式を使用します。  
  
 次の関数を呼び出すときに、パス式を指定する必要があります。  
  
-   **OPENJSON** を呼び出して、JSON データのリレーショナル ビューを作成します。 詳細については、「 [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)」をご覧ください。  
  
-   **JSON_VALUE** を呼び出して、JSON テキストから値を抽出します。 詳細については、「 [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)」をご覧ください。  
  
-   **JSON_QUERY** を呼び出して、JSON オブジェクトまたは配列を抽出します。 詳細については、「 [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)」をご覧ください。  
  
-   **JSON_MODIFY** を呼び出して、JSON 文字列内のプロパティの値を更新します。 詳細については、「 [JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md)」を参照してください。  

## <a name="parts-of-a-path-expression"></a>パス式の各部
 パス式には 2 つのコンポーネントがあります。  
  
1.  省略可能な[path モード](#PATHMODE)の値を持つ**lax**または**strict**です。  
  
2.  [パス](#PATH) 自体。  

##  <a name="PATHMODE"></a> Path mode  
 必要に応じて、パス式の先頭に **lax** または **strict**キーワードを指定してパス モードを宣言します。 既定値は **lax**です。  
  
-   **Lax**モードでは、この関数を返します空の値、パス式にエラーが含まれている場合。 たとえば、次の値を要求する**$.name**、JSON テキストが含まれていない、**名前**キー、関数は null を返しますが、エラーは発生しません。  
  
-   **Strict**モードでは、関数でエラーが発生、パス式にエラーが含まれている場合。  

次のクエリが明示的に指定`lax`パス式のモード。

```sql  
DECLARE @json NVARCHAR(MAX)
SET @json=N'{ ... }'

SELECT * FROM OPENJSON(@json, N'lax $.info')
```  
  
##  <a name="PATH"></a> Path  
 省略可能なパス モード宣言の後に、パス自体を指定します。  
  
-   ドル記号 (`$`) はコンテキスト アイテムを表します。  
  
-   プロパティのパスは、パス ステップのセットです。 パス ステップには、次の要素と演算子を含めることができます。  
  
    -   キー名。 たとえば、 `$.name` や `$."first name"`。 キー名がドル記号で始まるか、キー名にスペースなどの特殊文字が含まれている場合は、引用符で囲みます。   
  
    -   配列の要素。 たとえば、 `$.product[3]`のようにします。 配列は 0 から始まります。  
  
    -   ドット演算子 (`.`) は、オブジェクトのメンバーを示します。 たとえば、 `$.people[1].surname`、`surname`の子である`people`です。
  
## <a name="examples"></a>使用例  
 このセクションの例では、次の JSON テキストを参照します。  
  
```json  
{
    "people": [{
        "name": "John",
        "surname": "Doe"
    }, {
        "name": "Jane",
        "surname": null,
        "active": true
    }]
}
```  
  
 次の表に、パス式の例をいくつか示します。  
  
|パス式|値|  
|---------------------|-----------|  
|$.people[0].name|John|  
|$.people[1]|{ "name": "Jane",  "surname": null, "active": true }|  
|$.people[1].surname|null|  
|$|{ "people": [ { "name": "John",  "surname": "Doe" },<br />   { "name": "Jane",  "surname": null, "active": true } ] }|  
  
## <a name="how-built-in-functions-handle-duplicate-paths"></a>組み込み関数が重複するパスを処理する方法  
 JSON テキストには、重複するプロパティが含まれているのと同じレベルに同じ名前のキーを 2 つなどの場合、 **JSON_VALUE**と**JSON_QUERY**関数は、パスに一致する最初の値のみを返します。 重複するキーを含む JSON オブジェクトを解析し、すべての値を返すを使用して**OPENJSON**の次の例に示すようにします。  
  
```sql  
DECLARE @json NVARCHAR(MAX)
SET @json=N'{"person":{"info":{"name":"John", "name":"Jack"}}}'

SELECT value
FROM OPENJSON(@json,'$.person.info') 
```  

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>詳細については、組み込みの JSON が SQL Server のサポート  
特定のソリューションの多くは、ケース、および推奨事項を使用して、参照してください、[組み込みの JSON サポートに関するブログの投稿](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)SQL Server および Microsoft のプログラム マネージャー Jovan Popovic による Azure SQL データベースでします。
  
## <a name="see-also"></a>参照  
 [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)   
 [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)   
 [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)  
  
  

