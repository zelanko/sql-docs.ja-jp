---
title: XPath クエリ (SQLXML 4.0) に明示的な変換関数を指定する |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- explicit conversion functions [SQLXML]
- string function
- number function
- XPath queries [SQLXML], explicit conversion functions
ms.assetid: 1111cb5d-2bd9-4bdb-8de2-dc0e47452dd6
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 59a2a54b1a3fe7a8136fa2ab0cb56f4cd215c245
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083143"
---
# <a name="specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-40"></a>XPath クエリでの明示変換関数の指定 (SQLXML 4.0)
  次の例では、XPath クエリに明示変換関数を指定する方法を示します。 これらの例では、SampleSchema1.xml に格納されているマッピング スキーマに対して XPath クエリを指定しています。 このサンプル スキーマについては、次を参照してください。 [XPath の例のサンプル注釈付き XSD スキーマ&#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-use-the-number-explicit-conversion-function"></a>A. number() 明示変換関数を使用する  
 `number()` 関数は、引数を数値に変換します。  
  
 値を想定して**ContactID**は数値型以外は、次のクエリに変換**ContactID**数値にし値 4 と比較します。 クエリが、すべてを返します**\<従業員 >** 、コンテキスト ノードの子要素、 **ContactID** 4 の数値の値を持つ属性。  
  
```  
/child::Contact[number(attribute::ContactID)= 4]  
```  
  
 ショートカットを`attribute`軸 (@)、指定できるためと、`child`軸は、既定値、クエリから省略することができます。  
  
```  
/Contact[number(@ContactID) = 4]  
```  
  
 具体的で、クエリがである従業員を返します、 **ContactID**は 4 です。  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>マッピング スキーマに対して XPath クエリをテストするには  
  
1.  コピー、[サンプル スキーマ コード](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)し、テキスト ファイルに貼り付けます。 SampleSchema1.xml として保存します。  
  
2.  次のテンプレート (ExplicitConversionA.xml) を作成し、SampleSchema1.xml を保存したディレクトリに保存します。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Contact[number(@ContactID)=4]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、次を参照してください。 [SQLXML 4.0 クエリの実行に使用する ADO](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)です。  
  
 このテンプレートを実行の結果セットは。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
### <a name="b-use-the-string-explicit-conversion-function"></a>B. string() 明示変換関数を使用する  
 `string()` 関数は、引数を文字列に変換します。  
  
 次のクエリに変換**ContactID**で文字列値「4」と比較して、文字列にします。 クエリでは、すべてを返します**\<従業員 >** 、コンテキスト ノードの子要素、 **ContactID**文字列の値「4」。  
  
```  
/child::Contact[string(attribute::ContactID)="4"]  
```  
  
 ショートカットを`attribute`軸 (@)、指定できるためと、`child`軸は、既定値、クエリから省略することができます。  
  
```  
/Contact[string(@ContactID)="4"]  
```  
  
 機能的には、このクエリでは上の例のクエリと同じ結果が返されます。ただし、評価は数値 (4) ではなく文字列に対して行われます。  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>マッピング スキーマに対して XPath クエリをテストするには  
  
1.  コピー、[サンプル スキーマ コード](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)し、テキスト ファイルに貼り付けます。 SampleSchema1.xml として保存します。  
  
2.  次のテンプレート (ExplicitConversionB.xml) を作成し、SampleSchema1.xml を保存したディレクトリに保存します。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Contact[string(@ContactID)="4"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (SampleSchema1.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリの相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、次を参照してください。 [SQLXML 4.0 クエリの実行に使用する ADO](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)です。  
  
 このテンプレートを実行した場合の結果セットは次のとおりです。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
  