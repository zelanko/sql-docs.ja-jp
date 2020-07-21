---
title: XPath クエリでの明示的な変換関数の指定 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- explicit conversion functions [SQLXML]
- string function
- number function
- XPath queries [SQLXML], explicit conversion functions
ms.assetid: 1111cb5d-2bd9-4bdb-8de2-dc0e47452dd6
author: rothja
ms.author: jroth
ms.openlocfilehash: 07e2e67c1c30302c6d3e758f76805e92e509f6c4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85002869"
---
# <a name="specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-40"></a>XPath クエリでの明示変換関数の指定 (SQLXML 4.0)
  次の例では、XPath クエリに明示変換関数を指定する方法を示します。 これらの例では、SampleSchema1.xml に格納されているマッピング スキーマに対して XPath クエリを指定しています。 このサンプルスキーマの詳細については、「 [XPath のサンプルの注釈付き XSD スキーマの例 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)」を参照してください。  
  
## <a name="examples"></a>例  
  
### <a name="a-use-the-number-explicit-conversion-function"></a>A. number() 明示変換関数を使用する  
 `number()` 関数は、引数を数値に変換します。  
  
 **ContactID**の値が数値以外の場合、次のクエリは**ContactID**を数値に変換し、値4と比較します。 次に、クエリは **\<Employee>** コンテキストノードのすべての子要素を返します。 **ContactID**属性の数値は4です。  
  
```  
/child::Contact[number(attribute::ContactID)= 4]  
```  
  
 軸 (@) へのショートカットを `attribute` 指定できます `child` 。軸が既定値であるため、クエリから省略できます。  
  
```  
/Contact[number(@ContactID) = 4]  
```  
  
 関係用語では、クエリは**ContactID**が4の従業員を返します。  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>マッピング スキーマに対して XPath クエリをテストするには  
  
1.  [サンプルスキーマコード](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)をコピーし、テキストファイルに貼り付けます。 SampleSchema1.xml として保存します。  
  
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
  
     詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
 このテンプレート実行の結果セットは次のとおりです。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
### <a name="b-use-the-string-explicit-conversion-function"></a>B. string() 明示変換関数を使用する  
 `string()` 関数は、引数を文字列に変換します。  
  
 次のクエリでは、 **ContactID**を文字列に変換し、文字列値 "4" と比較します。 このクエリは、 **\<Employee>** コンテキストノードのすべての子要素を返します。文字列値が "4" の**ContactID**が返されます。  
  
```  
/child::Contact[string(attribute::ContactID)="4"]  
```  
  
 軸 (@) へのショートカットを `attribute` 指定できます `child` 。軸が既定値であるため、クエリから省略できます。  
  
```  
/Contact[string(@ContactID)="4"]  
```  
  
 機能的には、このクエリでは上の例のクエリと同じ結果が返されます。ただし、評価は数値 (4) ではなく文字列に対して行われます。  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>マッピング スキーマに対して XPath クエリをテストするには  
  
1.  [サンプルスキーマコード](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)をコピーし、テキストファイルに貼り付けます。 SampleSchema1.xml として保存します。  
  
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
  
     詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
 このテンプレートを実行した場合の結果セットは次のとおりです。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
  
