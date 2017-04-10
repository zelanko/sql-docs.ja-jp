---
title: "FOR JSON を使用してクエリ結果を JSON として書式設定する (SQL Server) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "01/31/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-json"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JSON の"
  - "JSON、エクスポート"
  - "JSON のエクスポート"
ms.assetid: 15b56365-58c2-496c-9d4b-aa2600eab09a
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# FOR JSON を使用してクエリ結果を JSON として書式設定する (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  SQL Server のデータを JSON としてエクスポートするか、または **FOR JSON** 句を **SELECT** ステートメントに追加して、クエリ結果を JSON として書式設定します。  
  
 **FOR JSON** 句を使用すると、出力の構造を明示的に指定したり、SELECT ステートメントの構造によって出力を決定したりできます。  
  
-   **FOR JSON 句で PATH モードを使用します**。 **FOR JSON** 句で **PATH** モードを使用すると、JSON 出力の形式を完全に制御できます。 ラッパー オブジェクトを作成して、複雑なプロパティを入れ子にすることができます。  
  
-   **FOR JSON 句で AUTO モードを使用します**。 **FOR JSON** 句で **AUTO** モードを使用すると、JSON 出力は、SELECT ステートメントの構造に基づいて自動的に書式設定されます。  
  
 **FOR JSON** 句を使用して、JSON 出力の形式設定をクライアント アプリケーションから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に委任します。 詳細については、「[SQL Server およびクライアント アプリでの FOR JSON 出力の使用 &#40;SQL Server&#41;](../../relational-databases/json/use-for-json-output-in-sql-server-and-in-client-apps-sql-server.md)」を参照してください。  
  
 ![FOR JSON](../../relational-databases/json/media/jsonslides2forjson.png "FOR JSON")  
  
## FOR JSON 句で PATH モードを使用する  
 **FOR JSON** 句で **PATH** モードを使用する例を以下に示します。

**PATH** モードではドット構文を使用できます。たとえば、ネストした出力を書式設定するには、`'Item.Price'` と指定します。 また、この例では、 **ROOT** オプションを使用して名前付きのルート要素を指定しています。  
-   詳細と例については、「[PATH モードで入れ子になった JSON 出力を書式設定する &#40;SQL Server&#41;](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md)」を参照してください。
-   構文と使用法については、「[FOR 句 &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)」を参照してください。  
  
 ![Diagram of flow of FOR JSON output](../../relational-databases/json/media/forjson-example1.png "Diagram of flow of FOR JSON output")  
  
## FOR JSON 句で AUTO モードを使用する  
 **FOR JSON** 句で **AUTO** モードを使用するサンプル クエリを以下に示します。

**AUTO** モードでは、SELECT ステートメントの構造によって JSON 出力の形式が決まります。 既定では、 **null** 値は出力に含まれません。 **INCLUDE_NULL_VALUES** を使用してこの動作を変更できます。  
  
-   詳細と例については、「[AUTO モードで自動的に JSON 出力を書式設定する &#40;SQL Server&#41;](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md)」を参照してください。
-   構文と使用法については、「[FOR 句 &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)」を参照してください。  
  
 **クエリ:**  
  
```tsql  
SELECT name, surname  
FROM emp  
FOR JSON AUTO  
```  
  
 **結果**  
  
```json  
[   
   { "name": "John" },  
   { "name": "Jane", "surname": "Doe" }  
]  
  
```  
  
## FOR JSON 句のオプションを使用して JSON 出力を制御する  
 **FOR JSON** 句の出力を制御するには、次のオプションを使用します。  
  
 [ROOT オプションを使用して JSON 出力にルート ノードを追加する &#40;SQL Server&#41;](../../relational-databases/json/add-a-root-node-to-json-output-with-the-root-option-sql-server.md)  
 JSON 出力に最上位の単一要素を追加するには、**ROOT** オプションを指定します。 指定しない場合、 **ROOT** オプションでは、JSON の出力はルート要素がないです。  
  
 [INCLUDE_NULL_VALUES オプションを使用して JSON の出力に Null 値を含める &#40;SQL Server&#41;](../../relational-databases/json/include-null-values-in-json-include-null-values-option.md)  
 JSON 出力に null 値を含めるには、**INCLUDE_NULL_VALUES** オプションを指定します。 このオプションを指定しない場合、出力では、クエリの結果での NULL 値を JSON のプロパティは含まれません。  
  
 [WITHOUT_ARRAY_WRAPPER オプションを使用して JSON 出力から角かっこを削除する &#40;SQL Server&#41;](../../relational-databases/json/remove square brackets from json - without_array_wrapper option.md)  
 既定で **FOR JSON** 句の JSON 出力を囲んでいる角かっこを削除するには、**WITHOUT_ARRAY_WRAPPER** オプションを指定します。 このオプションを使用すると、単一の JSON オブジェクトを出力として生成できます。 このオプションを指定しないと、JSON 出力が角かっこで囲まれます。  
  
 **FOR JSON** 句の出力に表示される内容の詳細については、このセクションの次のトピックを参照してください。  
  
 [FOR JSON が SQL Server データ型を JSON データ型に変換する方法 &#40;SQL Server&#41;](../../relational-databases/json/how-for-json-converts-sql-server-data-types-to-json-data-types-sql-server.md)  
 **FOR JSON** 句では、このトピックで説明する規則を使用して、JSON 出力で SQL データ型を JSON 型に変換します。  
  
 [FOR JSON での特殊文字のエスケープと制御文字 &#40;SQL Server&#41;](../../relational-databases/json/how-for-json-escapes-special-characters-and-control-characters-sql-server.md)  
 **FOR JSON** 句は、このトピックで説明する形式で JSON 出力の特殊文字をエスケープし、制御文字を表します。  
  
## FOR JSON 句の出力  
 **FOR JSON** 句の出力には、次の特徴があります。  
  
1.  結果セットには 1 つの列が含まれます。 小さな結果セットには 1 つの行が含まれます。 大きな結果セットには複数の行が含まれます。  
  
     ![Example of FOR JSON output](../../relational-databases/json/media/forjson-example2.png "Example of FOR JSON output")  
  
2.  結果は JSON オブジェクトの配列として書式設定されます。  
  
    -   配列に含まれる要素の数が、結果の行数になります。  
  
    -   結果セットの各行は、配列内で個別の JSON オブジェクトになります。  
  
    -   結果セットの各列は、JSON オブジェクトのプロパティになります。  
  
3.  列の名前とその値は、JSON の構文に従ってエスケープされます。  
  
 次の例は、JSON 出力の書式設定を示しています。  
  
 **クエリ結果**  
  
|||||  
|-|-|-|-|  
|**A**|**B**|**C**|**D**|  
|10|11|12|×|  
|20|21|22|Y|  
|30|31|32|Z|  
  
 **JSON 出力**  
  
```json  
[  
  { "A":10, "B":11, "C":12, "D":"X" },  
  { "A":20, "B":21, "C":22, "D":"Y" },  
  { "A":30, "B":31, "C":32, "D":"Z" }  
]  
```  
  
## SQL Server での FOR JSON と組み込みの JSON サポートの詳細情報  
 [Microsoft のプログラム マネージャー Jovan Popovic によるブログ記事](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
## 参照  
 [FOR 句 &#40;Transact-SQL&#41;](../Topic/FOR%20Clause%20\(Transact-SQL\).md)   
 [SQL Server およびクライアント アプリでの FOR JSON 出力の使用 &#40;SQL Server&#41;](../../relational-databases/json/use-for-json-output-in-sql-server-and-in-client-apps-sql-server.md)  
  
  