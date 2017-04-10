---
title: "JSON パス式 (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JSON、パス式"
  - "パス式 (JSON)"
ms.assetid: 25ea679c-84cc-4977-867c-2cbe9d192553
caps.latest.revision: 14
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 11
---
# JSON パス式 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  JSON オブジェクトのプロパティを参照するには、JSON パスを使用します。 JSON パスでは、Javascript に似た構文を使用します。  
  
 次の関数を呼び出すときに、パス式を指定する必要があります。  
  
-   **OPENJSON** を呼び出して、JSON データのリレーショナル ビューを作成します。 詳細については、「[OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)」をご覧ください。  
  
-   **JSON_VALUE** を呼び出して、JSON テキストから値を抽出します。 詳細については、「[JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)」をご覧ください。  
  
-   **JSON_QUERY** を呼び出して、JSON オブジェクトまたは配列を抽出します。 詳細については、「[JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)」をご覧ください。  
  
-   **JSON_MODIFY** を呼び出して、JSON 文字列内のプロパティの値を更新します。 詳細については、「[JSON_MODIFY &#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md)」をご覧ください。  
  
 パス式には 2 つのコンポーネントがあります。  
  
1.  省略可能な [パス モード](#PATHMODE)(lax または strict)。  
  
2.  [パス](#PATH) 自体。  
  
##  <a name="PATHMODE"></a> パス モード  
 必要に応じて、パス式の先頭に **lax** または **strict**キーワードを指定してパス モードを宣言します。 既定値は **lax**です。  
  
-   **lax** モードでは、パス式にエラーが含まれている場合、関数は空の値を返します。 たとえば、値 **$.name**を要求するときに JSON テキストに **name** キーが含まれていない場合、関数は null を返します。  
  
-   **strict** モードでは、パス式にエラーが含まれている場合、関数でエラーが発生します。  
  
##  <a name="PATH"></a> パス  
 省略可能なパス モード宣言の後に、パス自体を指定します。  
  
-   ドル記号 ($) はコンテキスト アイテムを表します。  
  
-   プロパティのパスは、パス ステップのセットです。 パス ステップには、次の要素と演算子を含めることができます。  
  
    -   キー名。 キー名がドル記号で始まるか、キー名にスペースなどの特殊文字が含まれている場合は、引用符で囲みます。 たとえば、 `$.name` や `$."first name"`。  
  
    -   配列の要素。 たとえば、`$.product[3]` のようにします。 配列は 0 から始まります。  
  
    -   ドット演算子 (.) は、オブジェクトのメンバーを示します。  
  
## 使用例  
 このセクションの例では、次の JSON テキストを参照します。  
  
```json  
{ "people":  
  [  
    { "name": "John", "surname": "Doe" },  
    { "name": "Jane", "surname": null, "active": true }  
  ]  
}  
```  
  
 次の表に、パス式の例をいくつか示します。  
  
|パス式|値|  
|---------------------|-----------|  
|$.people[0].name|John|  
|$.people[1]|{ "name": "Jane",  "surname": null, "active": true }|  
|$.people[1].surname|null|  
|$|{ "people": [ { "name": "John",  "surname": "Doe" },<br />   { "name": "Jane",  "surname": null, "active": true } ] }|  
  
## 重複するパスの処理方法  
 たとえば、同じ名前の 2 つのキーが同じレベルにある場合など、JSON テキストに重複するプロパティが含まれる場合、JSON_VALUE および JSON_QUERY 関数はパスに一致する最初の値を返します。 重複するキーが含まれる JSON オブジェクトを解析するには、次の例に示すように OPENJSON を使用します。  
  
```tsql  
DECLARE @json NVARCHAR(MAX) = N'{"person":{"info":{"name":"John", "name":"Jack"}}}'  
  
SELECT value FROM OPENJSON(@json, '$.person.info')  
```  
  
## 参照  
 [OPENJSON &#40;Transact-SQL&#41;](../../t-sql/functions/openjson-transact-sql.md)   
 [JSON_VALUE &#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)   
 [JSON_QUERY &#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)  
  
  