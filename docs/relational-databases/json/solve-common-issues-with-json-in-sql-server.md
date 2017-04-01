---
title: "SQL Server での JSON に関してよく寄せられる質問 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "07/07/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JSON、FAQ"
ms.assetid: feae120b-55cc-4601-a811-278ef1c551f9
caps.latest.revision: 9
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 9
---
# SQL Server での JSON に関してよく寄せられる質問
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

 SQL Server での組み込み JSON サポートに関する一般的な質問に対する回答をこちらで見つけることができます。  
 
## FOR JSON および JSON 出力

### FOR JSON PATH または FOR JSON AUTO?  
 **質問** 単一のテーブル上の単純な SQL クエリから JSON テキストの結果を作成する必要があります。 FOR JSON PATH および FOR JSON AUTO は、同じ出力を生成します。 これら 2 つのオプションのどちらを使用する必要がありますか。  
  
 **回答** FOR JSON PATH を使用します。 JSON の出力に違いはありませんが、AUTO モードには、列を入れ子にするかどうかを確認する追加のロジックがあります。 PATH を既定のオプションと見なします。  

### 入れ子になった JSON 構造の作成  
 **質問** 同じレベルで複数の配列を持つ複雑な JSON を生成する必要があります。 FOR JSON PATH では、パスを使用して入れ子になったオブジェクトを作成できます。また、FOR JSON AUTO では、テーブルごとに追加の入れ子になったレベルを作成します。 これら 2 つのオプションのどちらを使用しても、目的の出力を生成することができます。 既存のオプションが直接サポートしていないカスタムの JSON 形式を作成する方法はありますか。  
  
 **回答** 次の例で示すように、JSON テキストを返す列式として FOR JSON クエリを追加し、任意のデータ構造を作成するか、または JSON_QUERY 関数を使用して手動で JSON を作成することができます。  
  
```tsql  
SELECT col1, col2, col3,  
             (SELECT col11, col12, col13 FROM t11 WHERE t11.FK = t1.PK FOR JSON PATH) as t11,  
             (SELECT col21, col22, col23 FROM t21 WHERE t21.FK = t1.PK FOR JSON PATH) as t21,  
             (SELECT col31, col32, col33 FROM t31 WHERE t31.FK = t1.PK FOR JSON PATH) as t31,  
             JSON_QUERY('{"'+col4'":"'+col5+'"}' as t41  
FROM t1  
FOR JSON PATH  
```  
  
FOR JSON クエリまたは列式の JSON_QUERY 関数のすべての結果は、個別の入れ子になった JSON サブオブジェクトとして書式設定され、メインの結果に含まれます。  

### FOR JSON 出力内のダブルエスケープが指定された JSON を防ぐ  
 **質問** JSON テキストをテーブルの列に保存しました。 このテキストを FOR JSON の出力に含める必要があります。 FOR JSON では JSON 内のすべての文字をエスケープするため、次の例で示すように、入れ子になったオブジェクトではなく、JSON 文字列を取得しています。  
  
```tsql  
SELECT 'Text' as myText, '{"day":23}' as myJson  
FOR JSON PATH  
```  
  
 このクエリの結果は、次のようになります。  
  
```json  
[{"myText":"Text","myJson":"{\"day\":23}"}]  
```  
  
 この動作を回避する方法はありますか。 エスケープされたテキストではなく、JSON オブジェクトとして返される `{"day":23}` が必要です。  
  
 **回答** テキストの列またはリテラルに保存された JSON は、任意のテキストのように扱われます。 これは二重引用符で囲まれ、エスケープされます。 エスケープされない JSON オブジェクトとして返す場合は、次の例のように、この列を JSON_QUERY 関数に引数として渡す必要があります。  
  
```tsql  
SELECT col1, col2, col3, JSON_QUERY(jsoncol1) AS jsoncol1  
FROM tab1  
FOR JSON PATH  
```  
  
 省略可能な 2 番目のパラメーターのない JSON_QUERY は、結果として 1 番目の引数のみを返します。 JSON_QUERY は有効な JSON を返すため、FOR JSON は、この結果をエスケープする必要がないと認識します。

### WITHOUT_ARRAY_WRAPPER 句を使用して生成された JSON は、FOR JSON の出力でエスケープされます。  
 **質問** FOR JSON と WITHOUT_ARRAY_WRAPPER オプションを使用して、列式の書式設定を行おうとしています。  
  
```tsql  
SELECT 'Text' as myText,  
       (SELECT 12 day, 8 mon FOR JSON PATH, WITHOUT_ARRAY_WRAPPER) as myJson  
FOR JSON PATH   
```  
  
 FOR JSON クエリによって返された文字列は、プレーン テキストとしてエスケープされているようです。 これは、WITHOUT_ARRAY_WRAPPER が指定されている場合にのみ発生します。 どうして JSON オブジェクトとして扱われず、エスケープされないで結果に含まれないのですか?  
  
 **回答** WITHOUT_ARRAY_WRAPPER オプションを指定している場合は、生成された JSON テキストが有効である必要はありません。 そのため、他の FOR JSON では、これをプレーン テキストと見なし、文字列をエスケープします。 JSON の出力が有効であることが確実な場合は、次の例のように、JSON_QUERY 関数を使用してそれを囲み、正しく書式設定された JSON に昇格させます。  
  
```tsql  
SELECT 'Text' as myText,  
      JSON_QUERY((SELECT 12 day, 8 mon FOR JSON PATH, WITHOUT_ARRAY_WRAPPER)) as myJson  
FOR JSON PATH    
```  

## OPENJSON および JSON 入力

### OPENJSON のある JSON テキストから入れ子になった JSON サブオブジェクトを返す  
 **質問** 明示的なスキーマを持つ OPENJSON を使用して、スカラー値、オブジェクトおよび配列の両方を含む、複雑な JSON オブジェクトの配列を開くことができません。 WITH 句内のキーを参照する場合、スカラー値のみが返されます。 オブジェクトと配列は、null 値として返されます。 オブジェクトまたは JSON オブジェクトの配列を抽出する方法はありますか。  
  
 **回答** 列としてオブジェクトまたは配列を返す場合、次の例で示すように、列定義で AS JSON オプションを使用します。  
  
```tsql  
SELECT scalar1, scalar2, obj1, obj2, arr1  
FROM OPENJSON(@json)  
             WITH ( scalar1 int,  
                          scalar2 datetime2,  
                          obj1 NVARCHAR(MAX) AS JSON,  
                          obj2 NVARCHAR(MAX) AS JSON,  
                          arr1 NVARCHAR(MAX) AS JSON)  
```  

### 長いテキストの値を返すには、JSON_VALUE ではなく OPENJSON を使用します。  
 **質問** 長いテキストを含む JSON テキストに説明キーがあります。 `JSON_VALUE(@json, '$.description')` が、値の代わりに NULL を返します。  
  
 **回答** JSON_VALUE は小さいスカラー値を返すように設計されています。 一般的に、この関数はオーバーフロー エラーの代わりに NULL を返します。 より長い値を返す場合は、次の例のように、NVARCHAR(MAX) 値をサポートする OPENJSON を使用します。  
  
```tsql  
SELECT myText FROM OPENJSON(@json) WITH (myText NVARCHAR(MAX) '$.description')  
```  

### 重複するキーを処理するには、JSON_VALUE ではなく OPENJSON を使用します。  
 **質問** JSON テキストに重複するキーがあります。 JSON_VALUE は、パス上で見つかる最初のキーのみを返します。 同じ名前を持つすべてのキーを取得する方法はありますか。  
  
 **回答** JSON の組み込みスカラー関数は、最初に出現する参照先のオブジェクトのみを返します。 複数のキーが必要な場合は、次の例で示すように、OPENJSON テーブル値関数を使用します。  
  
```tsql  
SELECT value FROM OPENJSON(@json, '$.info.settings')  
WHERE [key] = 'color'  
```  

### OPENJSON には、互換性レベル 130 が必要です。  
 **質問** SQL Server 2016 で OPENJSON を実行しようとしていて、次のエラーが発生しています。  
  
 `Msg 208, Level 16, State 1 ‘Invalid object name OPENJSON’`  
  
 **回答** OPENJSON 関数は、互換性レベル 130 でのみ使用できます。 DB の互換性レベルが 130 より下の場合、OPENJSON は非表示になります。 他の JSON 関数は、すべての互換性レベルで使用できます。  
 
## その他の質問

### JSON テキストに英数字以外の文字を含む参照キー  
 **質問** JSON テキストのキーに英数字以外の文字があります。 これらのプロパティを参照する方法はありますか。  
  
 **回答** JSON パスでその文字を引用符で囲む必要があります。 たとえば、`JSON_VALUE(@json, '$."$info"."First Name".value')` のようにします。
 