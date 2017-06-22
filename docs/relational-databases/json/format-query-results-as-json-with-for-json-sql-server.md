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
ms.sourcegitcommit: 439b568fb268cdc6e6a817f36ce38aeaeac11fab
ms.openlocfilehash: 06095384c6f6ec876e0d103186b1269d19056987
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="format-query-results-as-json-with-for-json-sql-server"></a>FOR JSON を使用してクエリ結果を JSON として書式設定する (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

クエリ結果を JSON として書式設定するか、SQL Server のデータを JSON としてエクスポートするには、**FOR JSON** 句を **SELECT** ステートメントに追加します。 使用して、 **FOR JSON**アプリケーションを簡単にクライアントにクライアント アプリからの JSON 出力の書式を委任することによって句[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。
  
 **FOR JSON** 句を使用すると、出力の構造を明示的に指定したり、SELECT ステートメントの構造によって出力を決定したりできます。  
  
-   使用して**FOR JSON PATH** JSON 出力の形式を完全に制御を維持するためにします。 ラッパー オブジェクトを作成して、複雑なプロパティを入れ子にすることができます。  
  
-   使用して**FOR JSON AUTO** SELECT ステートメントの構造に基づいて、自動的に JSON 出力の書式を設定します。  
  
**FOR JSON** 句とその出力を使用した **SELECT** ステートメントの例を次に示します。
  
 ![JSON の](../../relational-databases/json/media/jsonslides2forjson.png "JSON の")  
  
## <a name="maintain-control-over-json-output-with-for-json-path"></a>FOR JSON PATH で JSON 出力を制御をします。
**PATH** モードではドット構文を使用できます。たとえば、ネストした出力を書式設定するには、 `'Item.Price'` と指定します。  

**FOR JSON** 句で **PATH** モードを使用するサンプル クエリを次に示します。 次の例では、**ROOT** オプションを使用して名前付きのルート要素を指定しています。 
  
 ![FOR JSON 出力のフロー図](../../relational-databases/json/media/forjson-example1.png "FOR JSON 出力のフロー図")  

### <a name="more-info"></a>詳細
詳細な情報と例についてを参照してください[入れ子になった JSON 出力を書式設定で PATH モード &#40;SQL Server &#41;](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md).

構文と使用法については、「 [FOR 句 &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)。  

## <a name="let-the-select-statement-control-json-output-with-for-json-auto"></a>FOR JSON AUTO で JSON 出力を SELECT ステートメントの制御を使用できます。
**AUTO** モードでは、SELECT ステートメントの構造によって JSON 出力の形式が決まります。 既定では、 **null** 値は出力に含まれません。 **INCLUDE_NULL_VALUES** を使用してこの動作を変更できます。  

**FOR JSON** 句で **AUTO** モードを使用するサンプル クエリを以下に示します。
 
**クエリ:**  
  
```sql  
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
詳細な情報と例についてを参照してください[形式自動的に JSON 出力で AUTO モード & #40 です。SQL Server &#41;](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md).

構文と使用法については、「 [FOR 句 &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)。  
  
## <a name="control-other-json-output-options"></a>他の JSON 出力オプションを制御する  
出力を制御、 **FOR JSON**次のオプションを使用して句。  
  
-   **ルート**です。 JSON 出力に最上位の単一要素を追加するには、 **ROOT** オプションを指定します。 このオプションを指定しない場合、JSON 出力にルート要素はありません。 詳細については、「 [ROOT オプションを使用して JSON 出力にルート ノードを追加する &#40;SQL Server&#41;](../../relational-databases/json/add-a-root-node-to-json-output-with-the-root-option-sql-server.md)。  
  
-   **INCLUDE_NULL_VALUES**です。 JSON 出力に null 値を含めるには、 **INCLUDE_NULL_VALUES** オプションを指定します。 このオプションを指定しない場合、出力、クエリの結果での NULL 値を JSON プロパティに含まれません。 詳細については、次を参照してください[INCLUDE_NULL_VALUES オプション &#40; を使用して JSON 出力に Null 値を含める。SQL Server &#41;](../../relational-databases/json/include-null-values-in-json-include-null-values-option.md).   

-   **WITHOUT_ARRAY_WRAPPER**です。 既定で **FOR JSON** 句の JSON 出力を囲んでいる角かっこを削除するには、 **WITHOUT_ARRAY_WRAPPER** オプションを指定します。 このオプションを使用して、1 行の結果からの出力として単一の JSON オブジェクトを生成します。 このオプションを指定しない場合は、JSON の出力が配列として書式設定 - は、角かっこで囲まれています。 詳細については、「 [WITHOUT_ARRAY_WRAPPER オプションを使用して JSON 出力から角かっこを削除する &#40;SQL Server&#41;](../../relational-databases/json/remove-square-brackets-from-json-without-array-wrapper-option.md)。 
   
## <a name="output-of-the-for-json-clause"></a>FOR JSON 句の出力  
 **FOR JSON** 句の出力には、次の特徴があります。  
  
1.  結果セットには 1 つの列が含まれます。
    -   小さな結果セットには 1 つの行が含まれます。
    -   大きな結果セットは、複数行にわたる長い JSON 文字列を分割します。
        -   既定では、SQL Server Management Studio (SSMS) を連結結果が単一行に出力の設定が**結果をグリッドに**です。 SSMS のステータス バーには、実際の行数が表示されます。
        -   他のクライアント アプリケーションは、複数の行の内容を組み合わせることで、長い結果を連結するコードを必要があります。 C# アプリケーションでこのコードの例は、次を参照してください。 [c# クライアント アプリで使用する FOR JSON 出力](https://docs.microsoft.com/en-us/sql/relational-databases/json/use-for-json-output-in-sql-server-and-in-client-apps-sql-server#use-for-json-output-in-a-c-client-app)です。
  
     ![FOR JSON 出力の例](../../relational-databases/json/media/forjson-example2.png "FOR JSON 出力の例")  
  
2.  結果は JSON オブジェクトの配列として書式設定されます。  
  
    -   JSON 配列内の要素の数は、(FOR JSON 句を適用) する前に、SELECT ステートメントの結果の行の数と同じです。 
  
    -   (FOR JSON 句を適用) する前に、SELECT ステートメントの結果の各行では、配列内の個別の JSON オブジェクトになります。  
  
    -   (FOR JSON 句が適用される) の前に、SELECT ステートメントの結果内の各列では、JSON オブジェクトのプロパティになります。  
  
3.  列の名前とその値は、JSON の構文に従ってエスケープされます。 詳細については、「 [FOR JSON での特殊文字のエスケープと制御文字 &#40;SQL Server&#41;](../../relational-databases/json/how-for-json-escapes-special-characters-and-control-characters-sql-server.md)。
  
### <a name="example"></a>例
示す例を次に示しますが、どのように**FOR JSON**句が JSON の出力を書式設定します。  
  
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

## <a name="learn-more-about-the-built-in-json-support-in-sql-server"></a>詳細については、組み込みの JSON が SQL Server のサポート  
特定のソリューションの多くは、ケース、および推奨事項を使用して、参照してください、[組み込みの JSON サポートに関するブログの投稿](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)SQL Server および Microsoft のプログラム マネージャー Jovan Popovic による Azure SQL データベースでします。
  
## <a name="see-also"></a>参照  
 [FOR 句 &#40;Transact-SQL&#41;](../../t-sql/queries/select-for-clause-transact-sql.md)   
 [SQL Server およびクライアント アプリでの FOR JSON 出力の使用 &#40;SQL Server&#41;](../../relational-databases/json/use-for-json-output-in-sql-server-and-in-client-apps-sql-server.md)  
  
  

