---
title: 一括読み込み (SQLXML 4.0) の XML のガイドラインと制限 |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XML Bulk Load [SQLXML], about XML Bulk Load
- bulk load [SQLXML], about bulk load
ms.assetid: c5885d14-c7c1-47b3-a389-455e99a7ece1
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1eea06d8be4d826315235836d2a1d47846381caf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68005348"
---
# <a name="guidelines-and-limitations-of-xml-bulk-load-sqlxml-40"></a>XML 一括読み込みのガイドラインと制限 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  XML 一括読み込みを使用する場合は、次のガイドラインと制限に留意してください。  
  
-   インライン スキーマはサポートされません。  
  
     インライン スキーマがソース XML ドキュメントにある場合、XML 一括読み込みでそのスキーマは無視されます。 XML 一括読み込みには、XML データの外部にあるマッピング スキーマを指定してください。 使用して、ノードには、マッピング スキーマを指定することはできません、 **xmlns ="x: schema"** 属性。  
  
-   XML ドキュメントが適切な形式であるかどうかはチェックされますが、検証は行われません。  
  
     XML 一括読み込みは、XML ドキュメントも整形式ことがあるかどうかを判断する場合は、XML が World Wide Web Consortium の XML 1.0 勧告の構文の要件に準拠していることを確認するかを確認します。 ドキュメントが適切な形式でない場合、XML 一括読み込みの処理は取り消され、エラーが返されます。 ただし、ドキュメントがフラグメントの場合 (ドキュメントに単一のルート要素がない場合) だけは、XML 一括読み込みでドキュメントが読み込まれます。  
  
     XML 一括読み込みでは、XML データ ファイル内で定義または参照されている XML-Data または DTD スキーマに関して、ドキュメントの検証は行われません。 さらに、XML 一括読み込みでは、指定されるマッピング スキーマに対して XML データ ファイルは検証されません。  
  
-   XML prolog 情報は無視されます。  
  
     XML 一括読み込み前に、と後のすべての情報を無視する、\<ルート > XML ドキュメント内の要素。 たとえば、XML 宣言、内部 DTD 定義、外部 DTD 参照、コメントなどは無視されます。  
  
-   マッピング スキーマで、2 つのテーブル (たとえば Customer と CustOrder) 間の主キー/外部キーのリレーションシップを定義する場合は、主キーがあるテーブルを先に記述する必要があります。 外部キー列があるテーブルは、後に記述します。 この理由は、テーブルがスキーマで識別される順序がデータベースに読み込みに使用される順序でことです。たとえば、次の XDR スキーマ エラーが発生ため、XML 一括読み込みで使用した場合、 **\<順序 >** 要素が前に説明した、 **\<顧客 >** 要素。 CustOrder の CustomerID 列は、Cust テーブル内の CustomerID 主キー列を参照する外部キー列です。  
  
    ```  
    <?xml version="1.0" ?>  
    <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
            xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
            xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
  
        <ElementType name="Order" sql:relation="CustOrder" >  
          <AttributeType name="OrderID" />  
          <AttributeType name="CustomerID" />  
          <attribute type="OrderID" />  
          <attribute type="CustomerID" />  
        </ElementType>  
  
       <ElementType name="CustomerID" dt:type="int" />  
       <ElementType name="CompanyName" dt:type="string" />  
       <ElementType name="City" dt:type="string" />  
  
       <ElementType name="root" sql:is-constant="1">  
          <element type="Customers" />  
       </ElementType>  
       <ElementType name="Customers" sql:relation="Cust"   
                         sql:overflow-field="OverflowColumn"  >  
          <element type="CustomerID" sql:field="CustomerID" />  
          <element type="CompanyName" sql:field="CompanyName" />  
          <element type="City" sql:field="City" />  
          <element type="Order" >   
               <sql:relationship  
                   key-relation="Cust"  
                    key="CustomerID"  
                    foreign-key="CustomerID"  
                    foreign-relation="CustOrder" />  
          </element>  
       </ElementType>  
    </Schema>  
    ```  
  
-   スキーマを使用して、オーバーフロー列が指定しないかどうか、 **sql:overflow-フィールド**注釈、XML 一括読み込みは、XML ドキュメント内に存在するが、マッピング スキーマに記述されていないデータは無視されます。  
  
     XML 一括読み込みでは、XML データ ストリーム内に既知のタグが検出されると常に、指定のマッピング スキーマが適用されます。 XML ドキュメントに存在していてもスキーマに記述されていないデータは無視されます。 たとえば、マッピング スキーマについて説明しますが、 **\<顧客 >** 要素。 XML データ ファイルは、  **\<AllCustomers >** を囲むすべて (これは、スキーマでは説明しません) タグのルート、 **\<顧客 >** 要素。  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
      <Customer>...</Customer>  
       ...  
    </AllCustomers>  
    ```  
  
     この場合は、XML 一括読み込みは無視されます、  **\<AllCustomers >** 要素にマッピングして、 **\<顧客 >** 要素。 XML ドキュメントに存在していてもスキーマに記述されていない要素は無視されます。  
  
     含む別の XML ソース データ ファイル **\<順序 >** 要素。 この要素はマッピング スキーマには記述されていません。  
  
    ```  
    <AllCustomers>  
      <Customer>...</Customer>  
        <Order> ... </Order>  
        <Order> ... </Order>  
         ...  
      <Customer>...</Customer>  
        <Order> ... </Order>  
        <Order> ... </Order>  
         ...  
      ...  
    </AllCustomers>  
    ```  
  
     XML 一括読み込みでは、これらは無視されます **\<順序 >** 要素。 使用する場合は、 **sql:overflow-フィールド**注釈によりオーバーフロー列、XML 一括読み込み、列を識別するために、スキーマでは、このコラムですべての未使用データを格納します。  
  
-   CDATA セクションとエンティティ参照は、データベースに保存される前に、同等の文字列に変換されます。  
  
     この例での値がラップ CDATA セクション、  **\<City >** 要素。 XML 一括読み込みを挿入する前に文字列値 ("NY") を抽出、  **\<City >** 要素がデータベースにします。  
  
    ```  
    <City><![CDATA[NY]]> </City>  
    ```  
  
     XML 一括読み込みでは、エンティティ参照は保持されません。  
  
-   マッピング スキーマで属性に既定値が指定されており、その属性が XML ソース データに含まれていない場合、XML 一括読み込みでは既定値が使用されます。  
  
     次のサンプル XDR スキーマに既定値を割り当てます、 **HireDate**属性。  
  
    ```  
    <?xml version="1.0" ?>  
    <Schema xmlns="urn:schemas-microsoft-com:xml-data"   
            xmlns:dt="urn:schemas-microsoft-com:xml:datatypes"    
            xmlns:sql="urn:schemas-microsoft-com:xml-sql" >  
       <ElementType name="root" sql:is-constant="1">  
          <element type="Customers" />  
       </ElementType>  
  
       <ElementType name="Customers" sql:relation="Cust3" >  
          <AttributeType name="CustomerID" dt:type="int"  />  
          <AttributeType name="HireDate"  default="2000-01-01" />  
          <AttributeType name="Salary"   />  
  
          <attribute type="CustomerID" sql:field="CustomerID" />  
          <attribute type="HireDate"   sql:field="HireDate"  />  
          <attribute type="Salary"     sql:field="Salary"    />  
       </ElementType>  
    </Schema>  
    ```  
  
     この XML データで、 **HireDate**属性は、2 番目の見つからない **\<顧客 >** 要素。 XML 一括読み込みで 2 つ目を挿入するとき **\<顧客 >** 要素がデータベースに、スキーマで指定されている既定値を使用します。  
  
    ```  
    <ROOT>  
      <Customers CustomerID="1" HireDate="1999-01-01" Salary="10000" />  
      <Customers CustomerID="2" Salary="10000" />  
    </ROOT>  
    ```  
  
-   **Sql:url-エンコード**注釈がサポートされていません。  
  
     XML データ入力に URL を指定して、その場所からデータの一括読み込みを行うことはできません。  
  
     マッピング スキーマで指定されているテーブルは、新しく作成されます (データベースは存在する必要があります)。 1 つ以上のテーブルが既に存在するデータベースの場合 SGDropTables プロパティは、これらの既存のテーブルを削除して再作成するかどうかを決定します。  
  
-   SchemaGen プロパティを指定する場合 (たとえばを SchemaGen = true)、マッピング スキーマで指定されているテーブルが作成されます。 ただし、SchemaGen が 1 つの例外でこれらのテーブル (PRIMARY KEY/FOREIGN KEY 制約) など、制約を作成できません。リレーションシップの主キーを構成する XML ノードが XML 型の ID を持つものとして定義されているかどうか (つまり、**型 ="xsd:ID"** XSD の) SGUseID プロパティを SchemaGen、True に設定しからの主キーの作成だけでなくID に、ノードが型指定は、マッピング スキーマ リレーションシップから主キー/外部キーのリレーションシップが作成されます。  
  
-   SchemaGen は使いません XSD スキーマ ファセットと機能拡張、リレーショナルを生成する[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]スキーマ。  
  
-   SchemaGen プロパティを指定する場合 (たとえばを SchemaGen = true) 一括読み込みで、テーブル (とのみ共有名のビューではない) が指定されている更新されます。  
  
-   SchemaGen は、注釈付き XSD からリレーショナル スキーマを生成するための基本的な機能のみを提供します。 ユーザーは必要に応じて、生成されたテーブルを手動で変更する必要があります。  
  
-   SchemaGen、テーブル間のリレーションシップを 1 つの存在を 2 つのテーブル間に関連するすべてのキーを含む 1 つのリレーションシップを作成しようとします。 この制限は、[!INCLUDE[tsql](../../../includes/tsql-md.md)] エラーの原因となることがあります。  
  
-   データベースに XML データの一括読み込みを行う場合は、マッピング スキーマ内に、データベース列にマップされる属性または子要素が 1 つ以上存在している必要があります。  
  
-   XML 一括読み込みを使用して日付値を挿入する場合、値は (-)CCYY-MM-DD((+-)TZ) の形式で指定する必要があります。 これは日付の標準の XSD 形式です。  
  
-   一部のプロパティ フラグは、他のプロパティ フラグと互換性がありません。 たとえば、一括読み込みはサポートされません**Ignoreduplicatekeys = true**と共に**Keepidentity = false**します。 ときに**Keepidentity = false**、一括読み込みでキーの値を生成するサーバーを必要があります。 テーブルが必要、 **IDENTITY**キーの制約。 サーバーは重複するキーを生成しない必要はありませんつまり**Ignoreduplicatekeys**に設定する**true**します。 **Ignoreduplicatekeys**に設定する必要があります**true**のみ行を持つテーブルに、受信データから主キーの値をアップロードするときに、主キー値の競合が発生する可能性があります。  
  
  
