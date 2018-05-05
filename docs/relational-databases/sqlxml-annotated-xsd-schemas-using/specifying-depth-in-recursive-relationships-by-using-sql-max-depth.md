---
title: Sql:max を使用して、再帰リレーションシップの深さを指定する-深さ |Microsoft ドキュメント
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
- max-depth annotation
- XPath queries [SQLXML], recursive relationships
- depth in recursive relationships [SQLXML]
- annotated XSD schemas, recursive relationships
- relationships [SQLXML], recursive relationships
- self joins
- recursive relationships [SQLXML]
- recursion [SQLXML]
- sql:max-depth
- recursive joins [SQLXML]
ms.assetid: 0ffdd57d-dc30-44d9-a8a0-f21cadedb327
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 025ad34e3aca3ea4330c9a5878f834c605bf645c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="specifying-depth-in-recursive-relationships-by-using-sqlmax-depth"></a>sql:max-depth を使用した、再帰リレーションシップの深さの指定
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  リレーショナル データベースでは、テーブルのリレーションシップにそのテーブル自身が含まれることを、再帰リレーションシップと呼びます。 たとえば、監督者と被監督者のリレーションシップでは、従業員の記録を格納するテーブルのリレーションシップに、そのテーブル自身が含まれます。 この場合、従業員テーブルはリレーションシップの 1 つの側では監督者となり、別の側では被監督者となります。  
  
 マッピング スキーマには、要素とその先祖が同じ型の再帰リレーションシップを含めることができます。  
  
## <a name="example-a"></a>例 A  
 次のテーブルを考えてみます。  
  
```  
Emp (EmployeeID, FirstName, LastName, ReportsTo)  
```  
  
 このテーブルでは、ReportsTo 列にマネージャーの従業員 ID が格納されています。  
  
 ここで従業員の XML 階層を生成して、次のサンプル XML フラグメントに示すように、マネージャーである従業員を階層の一番上に、マネージャーに報告を行う従業員をそれに対応する階層に表示したいとします。 どのようなこのを示していますが、*再帰ツリー*従業員 1 にします。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
     <Emp FirstName="Andrew" EmployeeID="2" LastName="Fuller" />   
     <Emp FirstName="Janet" EmployeeID="3" LastName="Leverling">  
        <Emp FirstName="Margaret" EmployeeID="4" LastName="Peacock">  
          <Emp FirstName="Steven" EmployeeID="5" LastName="Devolio">  
...  
...  
</root>  
```  
  
 このフラグメントでは、従業員 5 が従業員 4、従業員 4 が従業員 3 に、従業員 3 と 2 は従業員 1 に報告を行います。  
  
 この結果を生成するには、次の XSD スキーマを使用して、これに対する XPath クエリを指定できます。 スキーマでは、記述、  **\<Emp >** から成る EmployeeType 型の要素、  **\<Emp >** 同じ EmployeeType 型の子要素です。 これは、要素とその先祖が同じ型の再帰リレーションシップです。 さらに、スキーマを使用して、  **\<sql:relationship >** 監督者と被間の親子リレーションシップを記述します。 これで **\<sql:relationship >** Emp は親と子テーブルの両方です。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"  
                                  parent="Emp"  
                                  parent-key="EmployeeID"  
                                  child="Emp"  
                                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp" type="EmployeeType"   
                          sql:relation="Emp"   
                          sql:key-fields="EmployeeID"   
                          sql:limit-field="ReportsTo" />  
  <xsd:complexType name="EmployeeType">  
    <xsd:sequence>  
      <xsd:element name="Emp" type="EmployeeType"   
                              sql:relation="Emp"   
                              sql:key-fields="EmployeeID"  
                              sql:relationship="SupervisorSupervisee"  
                              sql:max-depth="6" />  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:ID" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 このリレーションシップは再帰的なので、何らかの方法でスキーマ内の再帰の深さを指定する必要があります。 指定しない場合、結果は無限再帰となり、従業員から次の従業員へと無限に報告を行うことになります。 **Sql:max-深さ**注釈では、元に再帰の深さを指定することができます。 値を指定する、この例では**sql:max-深さ**会社の管理階層の移動を深さを知る必要があります。  
  
> [!NOTE]  
>  スキーマを指定します、 **sql:limit-フィールド**の注釈が指定されていません、 **sql:limit-値**注釈。 これにより、結果として生成される階層の一番上のノードは、だれにも報告しない従業員だけになります  (ReportsTo は NULL です)。指定する**sql:limit-フィールド**を指定しないと**sql:limit-値**(を既定値は NULL) 注釈でこれを行います。 ツリー (テーブル内の各従業員のレポートのツリー) を削除する場合は、結果の XML に含めるすべての可能な報告、 **sql:limit-フィールド**スキーマから注釈。  
  
> [!NOTE]  
>  次の手順では、tempdb データベースを使用します。  
  
#### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>スキーマに対してサンプル XPath クエリをテストするには  
  
1.  仮想ルートが示す tempdb データベースに、Emp という名前のサンプル テーブルを作成します。  
  
    ```  
    USE tempdb  
    CREATE TABLE Emp (  
           EmployeeID int primary key,   
           FirstName  varchar(20),   
           LastName   varchar(20),   
           ReportsTo int)  
    ```  
  
2.  次のサンプル データを追加します。  
  
    ```  
    INSERT INTO Emp values (1, 'Nancy', 'Devolio',NULL)  
    INSERT INTO Emp values (2, 'Andrew', 'Fuller',1)  
    INSERT INTO Emp values (3, 'Janet', 'Leverling',1)  
    INSERT INTO Emp values (4, 'Margaret', 'Peacock',3)  
    INSERT INTO Emp values (5, 'Steven', 'Devolio',4)  
    INSERT INTO Emp values (6, 'Nancy', 'Buchanan',5)  
    INSERT INTO Emp values (7, 'Michael', 'Suyama',6)  
    ```  
  
3.  上のスキーマのコードをコピーして、テキスト ファイルに貼り付け、 maxDepth.xml として保存します。  
  
4.  次のテンプレートをコピーして、テキスト ファイルに貼り付け、 maxDepth.xml を保存したディレクトリに maxDepthT.xml としてファイルを保存します。 このテンプレートのクエリでは、Emp テーブル内のすべての従業員が返されます。  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="maxDepth.xml">  
        /Emp  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     マッピング スキーマ (maxDepth.xml) に指定するディレクトリ パスは、テンプレートを保存するディレクトリに対する相対パスです。 次のように、絶対パスを指定することもできます。  
  
    ```  
    mapping-schema="C:\MyDir\maxDepth.xml"  
    ```  
  
5.  SQLXML 4.0 テスト スクリプト (sqlxml4test.vbs) を作成し、それを使用してテンプレートを実行します。 詳細については、次を参照してください。 [SQLXML 4.0 クエリの実行に使用する ADO](../../relational-databases/sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)です。  
  
 結果を次に示します。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
  <Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
  <Emp FirstName="Andrew" EmployeeID="2" LastName="Fuller" />   
    <Emp FirstName="Janet" EmployeeID="3" LastName="Leverling">  
      <Emp FirstName="Margaret" EmployeeID="4" LastName="Peacock">  
        <Emp FirstName="Steven" EmployeeID="5" LastName="Devolio">  
          <Emp FirstName="Nancy" EmployeeID="6" LastName="Buchanan">  
            <Emp FirstName="Michael" EmployeeID="7" LastName="Suyama" />   
          </Emp>  
        </Emp>  
      </Emp>  
    </Emp>  
  </Emp>  
</root>  
```  
  
> [!NOTE]  
>  結果の階層の深さを生成するには、値を変更、 **sql:max-深さ**スキーマの注釈とそれぞれの変更後にもう一度、テンプレートを実行します。  
  
 上のスキーマでは、すべて、  **\<Emp >** 要素がまったく同じ属性のセット (**EmployeeID**、 **FirstName**、および**LastName**)。 次のスキーマが返す、さらに若干変更されて**ReportsTo**すべての属性、  **\<Emp >** マネージャーに報告する要素。  
  
 たとえば、次の XML フラグメントでは、従業員 1 の部下が示されています。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<root>  
<Emp FirstName="Nancy" EmployeeID="1" LastName="Devolio">  
  <Emp FirstName="Andrew" EmployeeID="2"   
       ReportsTo="1" LastName="Fuller" />   
  <Emp FirstName="Janet" EmployeeID="3"   
       ReportsTo="1" LastName="Leverling">  
...  
...  
```  
  
 変更後のスキーマは次のようになります。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:documentation>  
      Customer-Order-Order Details Schema  
      Copyright 2000 Microsoft. All rights reserved.  
    </xsd:documentation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"   
                  parent="Emp"  
                  parent-key="EmployeeID"  
                  child="Emp"  
                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp"   
                   type="EmpType"   
                   sql:relation="Emp"   
                   sql:key-fields="EmployeeID"   
                   sql:limit-field="ReportsTo" />  
  <xsd:complexType name="EmpType">  
    <xsd:sequence>  
       <xsd:element name="Emp"   
                    type="EmpType"   
                    sql:relation="Emp"   
                    sql:key-fields="EmployeeID"  
                    sql:relationship="SupervisorSupervisee"  
                    sql:max-depth="6"/>  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:int" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
    <xsd:attribute name="ReportsTo" type="xsd:int" />  
  </xsd:complexType>  
</xsd:schema>  
```  
  
## <a name="sqlmax-depth-annotation"></a>sql:max-depth 注釈  
 再帰リレーションシップで構成されるスキーマでは、スキーマ内に再帰の深さを明示的に指定する必要があります。 これは、対応する FOR XML EXPLICIT クエリを正常に作成し、要求された結果を返すために必要です。  
  
 使用して、 **sql:max-深さ**スキーマに記述されている再帰リレーションシップで再帰の深さを指定するスキーマの注釈。 値、 **sql:max-深さ**注釈は再帰の数を示す正の整数 (1 ~ 50): 1 の値は、対象の要素で再帰を停止、 **sql:max-深さ**注釈指定します。2 の値を要素から、[次へ] レベルで再帰を停止する**sql:max-深さ**; 指定されなどです。  
  
> [!NOTE]  
>  この基本となる実装では、マッピング スキーマに対して指定されている XPath クエリが、SELECT ... FOR XML EXPLICIT クエリに変換されます。 このクエリでは、再帰に有限の深さを指定する必要があります。 に対して指定した値が高い**sql:max-深さ**が大きいほど、FOR XML EXPLICIT クエリを生成されます。 これによって、取得に時間がかかることがあります。  
  
> [!NOTE]  
>  アップデートグラムと XML 一括読み込みでは、max-depth 注釈は無視されます。 つまり、再帰更新や再帰挿入は、max-depth に指定されている値に関係なく行われます。  
  
## <a name="specifying-sqlmax-depth-on-complex-elements"></a>複合要素での sql:max-depth の指定  
 **Sql:max-深さ**複雑なコンテンツ要素に注釈を指定することができます。  
  
### <a name="recursive-elements"></a>再帰要素  
 場合**sql:max-深さ**親要素と、再帰リレーションシップの子要素の両方で指定された、 **sql:max-深さ**親で指定されている注釈が優先されます。 たとえば、次のスキーマで、 **sql:max-深さ**親と子の従業員要素に注釈を指定します。 この場合、 **sql:max-深さ = 4**に指定されている、  **\<Emp >** 親要素 (監督者) が優先されます。 **Sql:max-深さ**の子で指定された **\<Emp >** 要素 (被監督者) は無視されます。  
  
#### <a name="example-b"></a>例 B  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"  
                                  parent="Emp"  
                                  parent-key="EmployeeID"  
                                  child="Emp"  
                                  child-key="ReportsTo" />  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp" type="EmployeeType"   
                          sql:relation="Emp"   
                          sql:key-fields="EmployeeID"   
                          sql:limit-field="ReportsTo"   
                          sql:max-depth="3" />  
  <xsd:complexType name="EmployeeType">  
    <xsd:sequence>  
      <xsd:element name="Emp" type="EmployeeType"   
                              sql:relation="Emp"   
                              sql:key-fields="EmployeeID"  
                              sql:relationship="SupervisorSupervisee"  
                              sql:max-depth="2" />  
    </xsd:sequence>   
    <xsd:attribute name="EmployeeID" type="xsd:ID" />  
    <xsd:attribute name="FirstName" type="xsd:string"/>  
    <xsd:attribute name="LastName" type="xsd:string"/>  
  </xsd:complexType>  
</xsd:schema>  
```  
  
 このスキーマをテストするには、サンプル A は、このトピックの前半に記載されている手順に従います。  
  
### <a name="nonrecursive-elements"></a>非再帰要素  
 場合、 **sql:max-深さ**再帰が発生しないスキーマ内の要素に注釈が指定されて、これは無視されます。 次のスキーマで、  **\<Emp >** 要素から成る、 **\<定数 >** が含まれている子要素、  **\<Emp >** 子要素です。  
  
 このスキーマで、 **sql:max-深さ**で指定されている注釈、 **\<定数 >** 間に再帰がないために、要素は無視されます、  **\<Emp>** 親と**\<定数 >** 子要素です。 間に再帰が、  **\<Emp >** 先祖と **\<Emp >** 子。 スキーマを指定します、 **sql:max-深さ**両方での注釈。 したがって、 **sql:max-深さ**、先祖に対して指定されている注釈 (**\<Emp >** 監督) が優先されます。  
  
#### <a name="example-c"></a>例 C  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:annotation>  
    <xsd:appinfo>  
      <sql:relationship name="SupervisorSupervisee"   
                  parent="Emp"   
                  child="Emp"   
                  parent-key="EmployeeID"   
                  child-key="ReportsTo"/>  
    </xsd:appinfo>  
  </xsd:annotation>  
  <xsd:element name="Emp"   
               sql:relation="Emp"   
               type="EmpType"  
               sql:limit-field="ReportsTo"  
               sql:max-depth="1" />  
    <xsd:complexType name="EmpType" >  
      <xsd:sequence>  
       <xsd:element name="Constant"   
                    sql:is-constant="1"   
                    sql:max-depth="20" >  
         <xsd:complexType >  
           <xsd:sequence>  
            <xsd:element name="Emp"   
                         sql:relation="Emp" type="EmpType"  
                         sql:relationship="SupervisorSupervisee"   
                         sql:max-depth="3" />  
         </xsd:sequence>  
         </xsd:complexType>  
         </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="EmployeeID" type="xsd:int" />  
    </xsd:complexType>  
</xsd:schema>  
```  
  
 このスキーマをテストするには、このトピックの例 A の手順に従ってください。  
  
## <a name="complex-types-derived-by-restriction"></a>制限により派生する複合型  
 により派生する複合型があれば**\<制限 >**、対応する基本複合型の要素を指定できません、 **sql:max-深さ**注釈。 このような場合、 **sql:max-深さ**派生型の要素に注釈を追加することができます。  
  
 その一方で、により派生する複合型がある場合**\<拡張子 >**、対応する基本複合型の要素を指定できます、 **sql:max-深さ**注釈。  
  
 に、次の XSD スキーマがエラーを生成するなど、 **sql:max-深さ**基本データ型に注釈を指定します。 によって派生した型では、この注釈はサポートされていません**\<制限 >** 別の型から。 この問題を解決するには、スキーマを変更し、を指定する必要があります、 **sql:max-深さ**派生型の要素の注釈。  
  
#### <a name="example-d"></a>例 D  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:dt="urn:schemas-microsoft-com:datatypes"  
            xmlns:msdata="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:complexType name="CustomerBaseType">   
    <xsd:sequence>  
       <xsd:element name="CID" msdata:field="CustomerID" />  
       <xsd:element name="CompanyName"/>  
       <xsd:element name="Customers" msdata:max-depth="3">  
         <xsd:annotation>  
           <xsd:appinfo>  
             <msdata:relationship  
                     parent="Customers"  
                     parent-key="CustomerID"  
                     child-key="CustomerID"  
                     child="Customers" />  
           </xsd:appinfo>  
         </xsd:annotation>  
       </xsd:element>  
    </xsd:sequence>  
  </xsd:complexType>  
  <xsd:element name="Customers" type="CustomerType"/>  
  <xsd:complexType name="CustomerType">  
    <xsd:complexContent>  
       <xsd:restriction base="CustomerBaseType">  
          <xsd:sequence>  
            <xsd:element name="CID"   
                         type="xsd:string"/>  
            <xsd:element name="CompanyName"   
                         type="xsd:string"  
                         msdata:field="CName" />  
            <xsd:element name="Customers"   
                         type="CustomerType" />  
          </xsd:sequence>  
       </xsd:restriction>  
    </xsd:complexContent>  
  </xsd:complexType>  
</xsd:schema>   
```  
  
 スキーマでは、 **sql:max-深さ**で指定された、 **CustomerBaseType**複合型。 スキーマで指定も、 **\<顧客 >** 型の要素**CustomerType**から派生した**CustomerBaseType**です。 このようなスキーマで指定された XPath クエリで、エラーが発生**sql:max-深さ**制限の基本型で定義されている要素でサポートされていません。  
  
## <a name="schemas-with-a-deep-hierarchy"></a>深い階層のスキーマ  
 要素に子要素が含まれ、その子要素にさらに別の子要素が含まれるというような深い階層のスキーマの場合は、 場合、 **sql:max-深さ**このようなスキーマで指定されている注釈を 500 個を超えるレベルをレベル 1、その子をレベル 2、およびなどで最上位の要素) の階層を含む XML ドキュメントを生成する、エラーが返されます。  
  
  
