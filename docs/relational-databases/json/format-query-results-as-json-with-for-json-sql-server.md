---
title: "FOR JSON を使用してクエリ結果を JSON として書式設定する (SQL Server) | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 01/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FOR JSON
- JSON, exporting
- exporting JSON
ms.assetid: 15b56365-58c2-496c-9d4b-aa2600eab09a
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c439a76e3e925d00e88adaaefa616e59f8529a40
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="format-query-results-as-json-with-for-json-sql-server"></a>FOR JSON を使用してクエリ結果を JSON として書式設定する (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

クエリ結果を JSON として書式設定するか、SQL Server のデータを JSON としてエクスポートするには、**FOR JSON** 句を **SELECT** ステートメントに追加します。 **FOR JSON** 句を使用して、JSON 出力の形式設定をクライアント アプリケーションから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に委任します。
  
 **FOR JSON** 句を使用すると、出力の構造を明示的に指定したり、SELECT ステートメントの構造によって出力を決定したりできます。  
  
-   JSON 出力の形式を完全に制御するには、**FOR JSON** 句で **PATH** モードを使用します。 ラッパー オブジェクトを作成して、複雑なプロパティを入れ子にすることができます。  
  
-   SELECT ステートメントの構造に基づいて自動的に JSON 出力を書式設定するには、**FOR JSON** 句で **AUTO** モードを使用します。  
  
**FOR JSON** 句とその出力を使用した **SELECT** ステートメントの例を次に示します。
  
 ![JSON の](../../relational-databases/json/media/jsonslides2forjson.png "JSON の")  
  
## <a name="maintain-control-over-json-output-with-path-mode"></a>PATH モードで JSON 出力を制御する  
**PATH** モードではドット構文を使用できます。たとえば、ネストした出力を書式設定するには、 `'Item.Price'` と指定します。 次の例では、**ROOT** オプションを使用して名前付きのルート要素を指定しています。  

**FOR JSON** 句で **PATH** モードを使用するサンプル クエリを次に示します。
  
 ![FOR JSON 出力のフロー図](../../relational-databases/json/media/forjson-example1.png "FOR JSON 出力のフロー図")  

### <a name="more-info"></a>詳細
詳細と例については、「[PATH モードで入れ子になった JSON 出力を書式設定する &#40;SQL Server&#41;](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md)」を参照してください。

構文と使用法については、「 [FOR 句 &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)。  

## <a name="let-the-select-statement-control-json-output-with-auto-mode"></a>SELECT ステートメントで AUTO モードを使用して JSON 出力を制御する  
**AUTO** モードでは、SELECT ステートメントの構造によって JSON 出力の形式が決まります。 既定では、 **null** 値は出力に含まれません。 **INCLUDE_NULL_VALUES** を使用してこの動作を変更できます。  

**FOR JSON** 句で **AUTO** モードを使用するサンプル クエリを以下に示します。
 
**クエリ:**  
  
```tsql  
SELECT name, surname  
FROM emp  
FOR JSON AUTO  
```  
  
 **[結果]**  
  
```json  
[{
    "name": "John"
}, {
    "name": "Jane",
    "surname": "Doe"
}]
```  
### <a name="more-info"></a>詳細
詳細と例については、「[AUTO モードで自動的に JSON 出力を書式設定する &#40;SQL Server&#41;](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md)」を参照してください。

構文と使用法については、「 [FOR 句 &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)。  
  
## <a name="control-other-json-output-options"></a>他の JSON 出力オプションを制御する  
 **FOR JSON** 句の出力を制御するには、次のオプションを使用します。  
  
-   JSON 出力に最上位の単一要素を追加するには、 **ROOT** オプションを指定します。 指定しない場合、 **ROOT** オプションでは、JSON の出力はルート要素がないです。 詳細については、「 [ROOT オプションを使用して JSON 出力にルート ノードを追加する &#40;SQL Server&#41;](../../relational-databases/json/add-a-root-node-to-json-output-with-the-root-option-sql-server.md)。  
  
-   JSON 出力に null 値を含めるには、 **INCLUDE_NULL_VALUES** オプションを指定します。 このオプションを指定しない場合、出力では、クエリの結果での NULL 値を JSON のプロパティは含まれません。 詳細については、「[INCLUDE_NULL_VALUES オプションを使用して JSON の出力に Null 値を含める &#40;SQL Server&#41;](../../relational-databases/json/include-null-values-in-json-include-null-values-option.md)。   

-   既定で **FOR JSON** 句の JSON 出力を囲んでいる角かっこを削除するには、 **WITHOUT_ARRAY_WRAPPER** オプションを指定します。 このオプションを使用すると、単一の JSON オブジェクトを出力として生成できます。 このオプションを指定しないと、JSON 出力が角かっこで囲まれます。 詳細については、「 [WITHOUT_ARRAY_WRAPPER オプションを使用して JSON 出力から角かっこを削除する &#40;SQL Server&#41;](../../relational-databases/json/remove-square-brackets-from-json-without-array-wrapper-option.md)。 
   
## <a name="output-of-the-for-json-clause"></a>FOR JSON 句の出力  
 **FOR JSON** 句の出力には、次の特徴があります。  
  
1.  結果セットには 1 つの列が含まれます。 小さな結果セットには 1 つの行が含まれます。 大きな結果セットには複数の行が含まれます。  
  
     ![FOR JSON 出力の例](../../relational-databases/json/media/forjson-example2.png "FOR JSON 出力の例")  
  
2.  結果は JSON オブジェクトの配列として書式設定されます。  
  
    -   配列に含まれる要素の数が、結果の行数になります。  
  
    -   結果セットの各行は、配列内で個別の JSON オブジェクトになります。  
  
    -   結果セットの各列は、JSON オブジェクトのプロパティになります。  
  
3.  列の名前とその値は、JSON の構文に従ってエスケープされます。 詳細については、「 [FOR JSON での特殊文字のエスケープと制御文字 &#40;SQL Server&#41;](../../relational-databases/json/how-for-json-escapes-special-characters-and-control-characters-sql-server.md)。
  
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
[{
    "A": 10,
    "B": 11,
    "C": 12,
    "D": "X"
}, {
    "A": 20,
    "B": 21,
    "C": 22,
    "D": "Y"
}, {
    "A": 30,
    "B": 31,
    "C": 32,
    "D": "Z"
}] 
```  
 **FOR JSON** 句の出力に表示される内容の詳細については、次のトピックを参照してください。  
-   [FOR JSON が SQL Server データ型を JSON データ型に変換する方法 &#40;SQL Server&#41;](../../relational-databases/json/how-for-json-converts-sql-server-data-types-to-json-data-types-sql-server.md)  
**FOR JSON** 句では、このトピックで説明する規則を使用して、JSON 出力で SQL データ型を JSON 型に変換します。  

-   [FOR JSON での特殊文字のエスケープと制御文字 &#40;SQL Server&#41;](../../relational-databases/json/how-for-json-escapes-special-characters-and-control-characters-sql-server.md)  
 **FOR JSON** 句は、このトピックで説明する形式で JSON 出力の特殊文字をエスケープし、制御文字を表します。  

## <a name="learn-more-about-for-json-and-built-in-json-support-in-sql-server"></a>SQL Server での FOR JSON と組み込みの JSON サポートの詳細情報  
 [Microsoft のプログラム マネージャー Jovan Popovic によるブログ記事](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
## <a name="see-also"></a>参照  
 [FOR 句 &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)   
 [SQL Server およびクライアント アプリでの FOR JSON 出力の使用 &#40;SQL Server&#41;](../../relational-databases/json/use-for-json-output-in-sql-server-and-in-client-apps-sql-server.md)  
  
  

