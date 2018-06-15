---
title: データ型の強制変換と sql:datatype 注釈 (SQLXML 4.0) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: sqlxml
ms.reviewer: ''
ms.suite: sql
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- mapping data types [SQLXML]
- type attribute
- sql:datatype
- data types [SQLXML], converting
- annotated XSD schemas, mapping data types
- xsd:type
- datatype annotation
- converting data types [SQLXML]
- data types [SQLXML], mapping data types
- XSD schemas [SQLXML], mapping data types
ms.assetid: db192105-e8aa-4392-b812-9d727918c005
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 25685856bbb1b088f7c2825e27973915f850dea7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32974117"
---
# <a name="data-type-coercions-and-the-sqldatatype-annotation-sqlxml-40"></a>データ型の強制型変換と sql:datatype 注釈 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  XSD スキーマで、 **xsd:type**属性が要素または属性の XSD データ型を指定します。 XSD スキーマを使用したデータベースからのデータの抽出では、指定されているデータ型を使用して、データが書式設定されます。  
  
 スキーマを XSD 型を指定するだけでなく、Microsoft を指定することも[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型を使用して、 **sql:datatype**注釈。 **Xsd:type**と**sql:datatype**属性は、XSD データ型間のマッピングを制御および[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。  
  
## <a name="xsdtype-attribute"></a>xsd:type 属性  
 使用することができます、 **xsd:type** XML データ型を指定する属性または列にマップされる要素の属性です。 **Xsd:type**サーバーとも実行される XPath クエリから返されるドキュメントに影響します。 含むマッピング スキーマに対して XPath クエリを実行すると**xsd:type**、XPath クエリを処理するときに指定されたデータ型を使用しています。 XPath の使用方法の詳細については**xsd:type**を参照してください[から XPath データ型への XSD データ型のマッピング&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/mapping-xsd-data-types-to-xpath-data-types-sqlxml-4-0.md)です。  
  
 返されるドキュメントでは、すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型は文字列表記に変換されます。 また、データ型によっては追加の変換が必要です。 次の表に、各種に使用される変換**xsd:type**値。  
  
|XSD データ型|SQL Server の変換|  
|-------------------|---------------------------|  
|ブール値|CONVERT(bit, COLUMN)|  
|日付|LEFT(CONVERT(nvarchar(4000), COLUMN, 126), 10)|  
|decimal|CONVERT(money, COLUMN)|  
|id/idref/idrefs|id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)|  
|nmtoken/nmtokens|id-prefix + CONVERT(nvarchar(4000), COLUMN, 126)|  
|[時刻]|SUBSTRING(CONVERT(nvarchar(4000), COLUMN, 126), 1+CHARINDEX(N'T', CONVERT(nvarchar(4000), COLUMN, 126)), 24)|  
|他のすべて|追加の変換はありません。|  
  
> [!NOTE]  
>  によって返される値の一部[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して指定されている XML データ型と互換性がない可能性があります**xsd:type**かの変換ができないため、(たとえば、"XYZ"からへの変換、 **10 進数**データ型) 値がそのデータ型の範囲を超えているため、または (-100000 に変換するなど、 **UnsignedShort** XSD 型)。 互換性のない型を変換しようとすると、無効な XML ドキュメントが生成されるか、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーになる可能性があります。  
  
## <a name="mapping-from-sql-server-data-types-to-xsd-data-types"></a>SQL Server データ型から XSD データ型へのマッピング  
 次の表は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型から XSD データ型への明確なマッピングです。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 型がわかっている場合は、XSD スキーマで指定できる、対応する XSD 型をこの表で確認してください。  
  
|SQL Server データ型|XSD データ型|  
|--------------------------|-------------------|  
|**bigint**|**long**|  
|**[バイナリ]**|**base64Binary**|  
|**bit**|**boolean**|  
|**char**|**文字列**|  
|**datetime**|**dateTime**|  
|**decimal**|**decimal**|  
|**float**|**double**|  
|**image**|**base64Binary**|  
|**int**|**int**|  
|**money**|**decimal**|  
|**nchar**|**文字列**|  
|**ntext**|**文字列**|  
|**nvarchar**|**文字列**|  
|**numeric**|**decimal**|  
|**real**|**float**|  
|**smalldatetime**|**dateTime**|  
|**smallint**|**short**|  
|**smallmoney**|**decimal**|  
|**sql_variant**|**文字列**|  
|**sysname**|**文字列**|  
|**text**|**文字列**|  
|**timestamp**|**dateTime**|  
|**tinyint**|**unsignedByte**|  
|**varbinary**|**base64Binary**|  
|**varchar**|**文字列**|  
|**uniqueidentifier**|**文字列**|  
  
## <a name="sqldatatype-annotation"></a>sql:datatype 注釈  
 **Sql:datatype**注釈が指定に使用される、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。 この注釈場合に指定する必要があります。  
  
-   一括読み込みを行うには**dateTime** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XSD から列**dateTime**、**日付**、または**時間**型です。 この場合、指定する必要があります、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列のデータの型を使用して**sql:datatype ="dateTime"** です。 この規則はアップデートグラムにも当てはまります。  
  
-   列に一括読み込みを行う[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **uniqueidentifier**型と、XSD 値が中かっこが含まれる GUID ({および})。 指定すると**sql:datatype = uniqueidentifier**列に挿入される前に、中かっこが値から削除されます。 場合**sql:datatype**が指定されていない、値は、中かっこと、insert または update は失敗と共に送信されます。  
  
-   XML データ型**base64Binary**さまざまなマップ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型 (**バイナリ**、**イメージ**、または**varbinary**)。 XML データ型にマップする**base64Binary**特定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、データ型を使用して、 **sql:datatype**注釈。 この注釈では、属性のマップ先列の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を明示的に指定できます。 これは、データをデータベースに格納する場合に便利で、 指定して、 **sql:datatype**注釈を明示的に識別することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型。  
  
 通常を指定することをお勧め**sql:datatype**スキーマです。  
  
## <a name="examples"></a>使用例  
 次の例を使用した実際のサンプルを作成するには、特定の条件を満たす必要があります。 詳細については、次を参照してください。 [SQLXML の例を実行するための要件](../../relational-databases/sqlxml/requirements-for-running-sqlxml-examples.md)です。  
  
### <a name="a-specifying-xsdtype"></a>A. xsd:type を指定する  
 この方法を示します XSD**日付**を使用して指定された型を**xsd:type**スキーマ内の属性が結果の XML ドキュメントに影響します。 このスキーマでは、AdventureWorks データベース内の Sales.SalesOrderHeader テーブルの XML ビューが提供されます。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Order" sql:relation="Sales.SalesOrderHeader">  
     <xsd:complexType>  
       <xsd:attribute name="SalesOrderID" type="xsd:string" />   
       <xsd:attribute name="CustomerID"   type="xsd:string" />   
       <xsd:attribute name="OrderDate"    type="xsd:date" />   
       <xsd:attribute name="DueDate"  />   
       <xsd:attribute name="ShipDate"  type="xsd:time" />   
     </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 この XSD スキーマには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から日付値を返す 3 つの属性が含まれています。 それぞれの属性は次のとおりです。  
  
-   指定します**xsd:type 日付 =** 上、 **OrderDate**属性、によって返される値の日付部分[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の**OrderDate**属性が表示されます。  
  
-   指定します**xsd:type 時間 =** 上、 **ShipDate**属性、によって返される値の時刻部分[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の**ShipDate**属性が表示されます。  
  
-   指定されていない**xsd:type**上、 **DueDate**属性、によって返されるものと同じ値[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が表示されます。  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>スキーマに対してサンプル XPath クエリをテストするには  
  
1.  上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、 xsdType.xml として保存します。  
  
2.  次のテンプレートをコピーして、テキスト ファイルに貼り付け、 xsdType.xml を保存したディレクトリに xsdTypeT.xml として保存します。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="xsdType.xml">  
        /Order  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (xsdType.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\SqlXmlTest\xsdType.xml"  
    ```  
  
3.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。  
  
     詳細については、次を参照してください。 [SQLXML 4.0 クエリの実行に使用する ADO](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)です。  
  
 次に結果セットの一部を示します。  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="43659"   
         CustomerID="676"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
  <Order SalesOrderID="43660"   
         CustomerID="117"   
         OrderDate="2001-07-01"   
         DueDate="2001-07-13T00:00:00"   
         ShipDate="00:00:00" />   
 ...  
</ROOT>  
```  
  
 これは、同等の XDR スキーマです。  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  
<ElementType name="Order" sql:relation="Sales.SalesOrderHeader">  
    <AttributeType name="SalesOrderID" />  
    <AttributeType name="CustomerID"  />  
    <AttributeType name="OrderDate" dt:type="date" />  
    <AttributeType name="DueDate" />  
    <AttributeType name="ShipDate" dt:type="time" />  
  
    <attribute type="SalesOrderID" sql:field="OrderID" />  
    <attribute type="CustomerID" sql:field="CustomerID" />  
    <attribute type="OrderDate" sql:field="OrderDate" />  
    <attribute type="DueDate" sql:field="DueDate" />  
    <attribute type="ShipDate" sql:field="ShipDate" />  
</ElementType>  
</Schema>  
```  
  
### <a name="b-specifying-sql-data-type-using-sqldatatype"></a>B. sql:datatype を使用して SQL データ型を指定する  
 作業用サンプルについては、例 G を参照してください[XML 一括読み込みの例&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/xml-bulk-load-examples-sqlxml-4-0.md)です。 この例では、"{" および "}" を含む GUID 値の一括読み込みが行われます。 この例では、スキーマが指定**sql:datatype**を識別する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型として**uniqueidentifier**です。 この例ではいつ**sql:datatype**スキーマで指定する必要があります。  
  
  
