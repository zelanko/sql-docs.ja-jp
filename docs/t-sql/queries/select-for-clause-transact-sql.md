---
title: "FOR 句 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FOR
- FOR CLAUSE
- FOR_TSQL
- FOR_CLAUSE_TSQL
dev_langs: TSQL
helpviewer_keywords:
- XML option [SQL Server]
- BROWSE option
- FOR clause [Transact-SQL]
ms.assetid: 08a6f084-8f73-4f2a-bae4-3c7513dc99b9
caps.latest.revision: "54"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 51924cf8a6715e8966911b33c4c1cf691326322c
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="select---for-clause-transact-sql"></a>SELECT の FOR 句 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  FOR 句を使用すると、クエリ結果の次のオプションのいずれかを指定できます。  
  
-   指定してブラウズ モード カーソルでクエリ結果の表示中に更新を許可する**FOR BROWSE**です。  
  
-   クエリ結果を指定することによって XML として書式設定**FOR XML**です。  
  
-   指定して、クエリの結果を JSON として書式**FOR JSON**です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
[ FOR { BROWSE | <XML> | <JSON>} ]  
  
<XML> ::=  
XML   
{   
    { RAW [ ( 'ElementName' ) ] | AUTO }   
    [   
        <CommonDirectivesForXML>   
        [ , { XMLDATA | XMLSCHEMA [ ( 'TargetNameSpaceURI' ) ] } ]   
        [ , ELEMENTS [ XSINIL | ABSENT ]   
    ]  
  | EXPLICIT   
    [   
        <CommonDirectivesForXML>   
        [ , XMLDATA ]   
    ]  
  | PATH [ ( 'ElementName' ) ]   
    [  
        <CommonDirectivesForXML>   
        [ , ELEMENTS [ XSINIL | ABSENT ] ]  
    ]  
}   
  
<CommonDirectivesForXML> ::=   
[ , BINARY BASE64 ]  
[ , TYPE ]  
[ , ROOT [ ( 'RootName' ) ] ]  
  
<JSON> ::=  
JSON   
{   
    { AUTO | PATH }   
    [   
        [ , ROOT [ ( 'RootName' ) ] ]  
        [ , INCLUDE_NULL_VALUES ]  
        [ , WITHOUT_ARRAY_WRAPPER ]  
    ]  
  
}  
```  
  
## <a name="for-browse"></a>FOR BROWSE  
 BROWSE  
 DB-Library ブラウズ モード カーソルでデータを表示しているときに、更新が許可されます。 テーブルは、テーブルが含まれている場合、アプリケーションで参照できる、**タイムスタンプ**列、テーブル、一意のインデックスがあり、FOR BROWSE オプションがのインスタンスに送信される SELECT ステートメントの最後にある[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
> [!NOTE]  
>  使用することはできません、 \<lock_hint > HOLDLOCK、FOR BROWSE オプションを含む SELECT ステートメントでします。
  
 FOR BROWSE は、UNION 演算子によって結合された SELECT ステートメントでは使えません。  
  
> [!NOTE]  
>  テーブルの一意なインデックス キー列が NULL 値を許容し、かつそのテーブルが外部結合の内部にある場合、そのインデックスはブラウズ モードではサポートされません。  
  
 ブラウズ モードでは、行をスキャンしてできます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブルが表示され、一度に 1 行のテーブル内のデータを更新します。 アクセスする、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル ブラウズ モードで、アプリケーションで、次の 2 つのオプションのいずれかを使用する必要があります。  
  
-   SELECT ステートメントからデータにアクセスするために使用、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブルは、キーワードで終了する必要があります**FOR BROWSE**です。 有効にすると、 **FOR BROWSE**ブラウズ モードを使用するオプションで、一時テーブルが作成されます。  
  
-   次を実行する必要があります[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントを使用してブラウズ モードを有効にする、 **NO_BROWSETABLE**オプション。  
  
    ```  
    SET NO_BROWSETABLE ON  
    ```  
  
     有効にすると、 **NO_BROWSETABLE**オプションのすべての SELECT ステートメントの動作として、 **FOR BROWSE**オプションは、ステートメントに追加されます。 ただし、 **NO_BROWSETABLE**オプションはありません、一時テーブルを作成する、 **FOR BROWSE**オプション一般的に使用して、結果をアプリケーションに送信します。  
  
 データにアクセスしようとすると[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]内のテーブルが外部結合ステートメントを含む SELECT クエリを使用してモードを参照してブラウズ モードが sup ない外部結合ステートメントの内側にあるテーブルに一意のインデックスが定義されると、ポート、一意のインデックスです。 ブラウズ モードで一意のインデックスがサポートされるのは、すべての一意のインデックス キー列が NULL 値を使用できる場合のみです。 次の条件に当てはまる場合は、ブラウズ モードで一意のインデックスがサポートされません。  
  
-   データにアクセスしようとする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]内のテーブルが外部結合ステートメントを含む SELECT クエリを使用してモードを参照します。  
  
-   外部結合ステートメントの内部に存在するテーブルに一意のインデックスが定義されている場合。  
  
 ブラウズ モードでこの動作を再現するには、以下の手順を実行します。  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、SampleDB という名前のデータベースを作成します。  
  
2.  SampleDB データベースに tleft テーブルと tright テーブルを作成し、両方に c1 という単一列が含まれるようにします。 tleft テーブルの c1 列に一意のインデックスを定義し、この列が NULL 値を許容するように設定します。 これを行うには、次を実行[!INCLUDE[tsql](../../includes/tsql-md.md)]適切なクエリ ウィンドウ内のステートメント。  
  
    ```  
    CREATE TABLE tleft(c1 INT NULL UNIQUE) ;  
    GO   
    CREATE TABLE tright(c1 INT NULL) ;  
    GO  
    ```  
  
3.  tleft テーブルと tright テーブルに複数の値を挿入します。 tleft テーブルに NULL 値を挿入します。 これを行うには、次を実行[!INCLUDE[tsql](../../includes/tsql-md.md)]クエリ ウィンドウ内のステートメント。  
  
    ```  
    INSERT INTO tleft VALUES(2) ;  
    INSERT INTO tleft VALUES(NULL) ;  
    INSERT INTO tright VALUES(1) ;  
    INSERT INTO tright VALUES(3) ;  
    INSERT INTO tright VALUES(NULL) ;  
    GO  
    ```  
  
4.  オン、 **NO_BROWSETABLE**オプション。 これを行うには、次を実行[!INCLUDE[tsql](../../includes/tsql-md.md)]クエリ ウィンドウ内のステートメント。  
  
    ```  
    SET NO_BROWSETABLE ON ;  
    GO  
    ```  
  
5.  SELECT クエリで外部結合ステートメントを使用して、tleft テーブルと tright テーブルのデータにアクセスします。 tleft テーブルが外部結合ステートメントの内部に存在することを確認します。 これを行うには、次を実行[!INCLUDE[tsql](../../includes/tsql-md.md)]クエリ ウィンドウ内のステートメント。  
  
    ```  
    SELECT tleft.c1   
    FROM tleft   
    RIGHT JOIN tright   
    ON tleft.c1 = tright.c1   
    WHERE tright.c1 <> 2 ;  
  
    ```  
  
     [結果] ペインに、次の出力が表示されます。  
  
     c1  
  
     ---\-  
  
     NULL  
  
     NULL  
  
 ブラウズ モードで SELECT クエリを実行してテーブルにアクセスすると、右外部結合ステートメントの定義に従い、SELECT クエリの結果セットに tleft テーブルの c1 列の NULL 値が 2 つ格納されます。 したがって、結果セットではテーブルの NULL 値、および右外部結合ステートメントによって提供された NULL 値を区別できません。 結果セットの NULL 値を無視しなければならない場合、正しくない結果が返されることがあります。  
  
> [!NOTE]  
>  一意のインデックスに含まれる列で NULL 値を使用できない場合は、結果セットの NULL 値がすべて右外部結合ステートメントによって提供されます。  
  
## <a name="for-xml"></a>FOR XML  
 XML  
 クエリの結果を XML ドキュメントとして返します。 XML モードとして、RAW、AUTO、EXPLICIT のいずれか 1 つを指定する必要があります。 XML データの詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を参照してください[FOR XML &#40;です。SQL Server &#41;](../../relational-databases/xml/for-xml-sql-server.md).  
  
 RAW [ **('***ElementName***')** ]  
 クエリの結果を受け取り、汎用識別子を持つ XML 要素に結果セット内の各行を変換\<行/> 要素タグとして。 必要に応じて、その行要素に名前を指定することもできます。 結果の XML 出力が、指定した*ElementName*行ごとに生成される行要素として。 詳細については、次を参照してください。 [FOR XML での RAW モードの使用](../../relational-databases/xml/use-raw-mode-with-for-xml.md)と[FOR XML での RAW モードの使用](../../relational-databases/xml/use-raw-mode-with-for-xml.md)です。  
  
 AUTO  
 クエリの結果を単純な入れ子の XML ツリーで返します。 FROM 句に含まれる各テーブルは、そのうち少なくとも 1 つの列が SELECT 句の一覧に示され、XML 要素として表されます。 SELECT 句に一覧されている列は、該当する要素属性にマップされます。 詳細については、「 [FOR XML での AUTO モードの使用](../../relational-databases/xml/use-auto-mode-with-for-xml.md)」を参照してください。  
  
 EXPLICIT  
 結果として得られる XML ツリーの形状を明示的に定義することを指定します。 このモードを使用する場合は、目的の入れ子に関する追加の情報を明示的に指定できるように、クエリを特別な方法で記述する必要があります。 詳細については、「 [FOR XML での EXPLICIT モードの使用](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)」を参照してください。  
  
 XMLDATA  
 インライン XDR スキーマを返します。ただし、結果にルート要素は追加されません。 XMLDATA を指定すると、XDR スキーマはドキュメントに追加されます。  
  
> [!IMPORTANT]  
>  XMLDATA ディレクティブは推奨されません。 RAW モードと AUTO モードの場合は、XSD 世代を使用してください。 EXPLICIT モードでは、XMLDATA ディレクティブに代わる機能はありません。 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 XMLSCHEMA [ **('***TargetNameSpaceURI***')** ]  
 インライン XSD スキーマを返します。 このディレクティブを指定する場合は、必要に応じて、対象名前空間の URI を指定することもできます。指定した場合は、スキーマにある指定した名前空間が返されます。 詳細については、「 [Generate an Inline XSD Schema](../../relational-databases/xml/generate-an-inline-xsd-schema.md)」を参照してください。  
  
 ELEMENTS  
 列を副要素として返します。 指定していない場合は、XML 属性にマップされます。 このオプションは、RAW、AUTO、および PATH モードでのみサポートされます。 詳細については、「 [FOR XML での RAW モードの使用](../../relational-databases/xml/use-raw-mode-with-for-xml.md)」を参照してください。  
  
 XSINIL  
 指定を持つ要素**xsi:nil**属性に設定**True** NULL 列の値を作成します。 このオプションは、ELEMENTS ディレクティブでのみ指定できます。 詳細については、次を参照してください。 [XSINIL パラメーターで、NULL 値の要素の生成](../../relational-databases/xml/generate-elements-for-null-values-with-the-xsinil-parameter.md)です。  
  
 ABSENT  
 列の値が NULL の場合、対応する XML 要素を XML 結果に追加しません。 このオプションは、ELEMENTS でのみ指定してください。  
  
 PATH [ **('***ElementName***')** ]  
 生成、\<行 > 要素ラッパーを結果セット内の行ごとです。 必要に応じての要素名を指定することができます、\<行 > 要素ラッパーです。 FOR XML PATH など、空の文字列を提供するかどうか (**'**))、ラッパー要素は生成されません。 EXPLICIT ディレクティブを使用するよりも、PATH を使用した方が、クエリが単純になる場合があります。 詳細については、「 [FOR XML での PATH モードの使用](../../relational-databases/xml/use-path-mode-with-for-xml.md)」を参照してください。  
  
 BINARY BASE64  
 クエリは、バイナリ データをバイナリ ベース 64 エンコード形式で返します。 RAW モードおよび EXPLICIT モードでバイナリ データを取得する場合は、このオプションを指定する必要があります。 AUTO モードの場合は、これは既定値です。  
  
 TYPE  
 クエリとして結果を返すことを示す**xml**型です。 詳細については、「 [FOR XML クエリの TYPE ディレクティブ](../../relational-databases/xml/type-directive-in-for-xml-queries.md)」を参照してください。  
  
 ROOT [ **('***RootName***')** ]  
 単一のトップレベル要素を、結果として生成される XML に追加します。 必要に応じて、生成するルート要素名を指定することもできます。 省略可能なルートの名前が指定されていない場合、既定\<ルート > 要素を追加します。  
  
 詳細については、次を参照してください。 [FOR XML &#40;です。SQL Server &#41;](../../relational-databases/xml/for-xml-sql-server.md).  
  
 **XML の例**  
  
 次の例では、`FOR XML AUTO` を `TYPE` オプションおよび `XMLSCHEMA` オプションと共に指定しています。 ため、`TYPE`オプションが、結果セットとしてクライアントに返されます、 **xml**型です。 `XMLSCHEMA` オプションは、返される XML データにインライン XSD スキーマが含まれることを指定し、`ELEMENTS` オプションは、結果の XML が要素中心であることを指定します。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT p.BusinessEntityID, FirstName, LastName, PhoneNumber AS Phone  
FROM Person.Person AS p  
JOIN Person.PersonPhone AS pph ON p.BusinessEntityID  = pph.BusinessEntityID  
WHERE LastName LIKE 'G%'  
ORDER BY LastName, FirstName   
FOR XML AUTO, TYPE, XMLSCHEMA, ELEMENTS XSINIL;  
```  
  
## <a name="for-json"></a>JSON の  
 JSON  
 指定 FOR JSON クエリの結果を返すには、JSON テキストとして書式設定します。 また、次の JSON モードのいずれかを指定する必要がある: 自動またはパス。 詳細については、 **FOR JSON**句を参照してください[クエリ結果を FOR JSON &#40; を使用して、JSON として書式設定SQL Server &#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md).  
  
 AUTO  
 構造に基づいて、自動的に JSON 出力の形式、**選択**ステートメント  
            指定して**FOR JSON AUTO**です。 詳細と例については、「[AUTO モードで自動的に JSON 出力を書式設定する &#40;SQL Server&#41;](../../relational-databases/json/format-json-output-automatically-with-auto-mode-sql-server.md)」を参照してください。  
  
 PATH  
 指定して、JSON 出力の形式を完全に制御を取得します。   
            **FOR JSON PATH**です。 **PATH** モードでは、ラッパー オブジェクトを作成し、複雑なプロパティを入れ子にすることができます。 詳細と例については、「[PATH モードで入れ子になった JSON 出力を書式設定する &#40;SQL Server&#41;](../../relational-databases/json/format-nested-json-output-with-path-mode-sql-server.md)」を参照してください。  
  
 INCLUDE_NULL_VALUES  
 指定して、JSON 出力に null 値を含める、 **INCLUDE_NULL_VALUES**オプションは、 **FOR JSON**句。 このオプションを指定しない場合、出力は、クエリの結果に null 値を JSON のプロパティを含まれません。 詳細と例については、次を参照してください[INCLUDE_NULL_VALUES オプション &#40; を使用して JSON 出力に Null 値を含める。SQL Server &#41;](../../relational-databases/json/include-null-values-in-json-include-null-values-option.md).  
  
 ROOT [ **('***RootName***')** ]  
 指定して、JSON 出力に単一の最上位要素を追加、**ルート**オプションは、 **FOR JSON**句。 指定しない場合、 **ROOT** オプションでは、JSON の出力はルート要素がないです。 詳細と例については、次を参照してください[ROOT オプション &#40; で JSON 出力にルート ノードを追加。SQL Server &#41;](../../relational-databases/json/add-a-root-node-to-json-output-with-the-root-option-sql-server.md).  
  
 WITHOUT_ARRAY_WRAPPER  
 指定することによって、既定では、JSON 出力を囲んでいる角かっこを削除、 **WITHOUT_ARRAY_WRAPPER**オプションは、 **FOR JSON**句。 このオプションを指定しないと、JSON 出力が角かっこで囲まれます。 使用して、 **WITHOUT_ARRAY_WRAPPER**を出力として単一の JSON オブジェクトを生成するオプションです。  詳細については、「 [WITHOUT_ARRAY_WRAPPER オプションを使用して JSON 出力から角かっこを削除する &#40;SQL Server&#41;](../../relational-databases/json/remove-square-brackets-from-json-without-array-wrapper-option.md)。  
  
 詳細については、「[FOR JSON を使用してクエリ結果を JSON として書式設定する &#40;SQL Server&#41;](../../relational-databases/json/format-query-results-as-json-with-for-json-sql-server.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)  
  
  
