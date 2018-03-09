---
title: ".NET 環境での SQLXML 一括読み込みの使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQLXML, XML Bulk Load
- XML Bulk Load [SQLXML], .NET environment
- .NET Framework [SQLXML], XML Bulk Load
- bulk load [SQLXML], .NET environment
ms.assetid: b85df83b-ba56-43bf-bcdf-b2a6fca43276
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4c7e12a75ecd120c99a2e658c47acb8b28ffb260
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="sqlxml-40-net-framework-support---using-bulk-load"></a>SQLXML 4.0 の .NET Framework のサポートの一括読み込みの使用
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
ここでは、XML 一括読み込み機能を .NET 環境で使用する方法について説明します。 XML 一括読み込みの詳細については、次を参照してください。 [XML データの一括読み込みを実行する &#40;です。SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md).  
  
 マネージ環境から SQLXML 一括読み込み COM オブジェクトを使用するには、このオブジェクトにプロジェクト参照を追加する必要があります。 これによって、一括読み込み COM オブジェクトのマネージ ラッパー インターフェイスが生成されます。  
  
> [!NOTE]  
>  マネージ XML 一括読み込みはマネージ ストリームでは動作せず、ネイティブ ストリームのラッパーが必要です。 SQLXML 一括読み込みコンポーネントはマルチスレッド環境 ('[MTAThread]' 属性) では動作しません。 次の追加情報を使用して InvalidCastException 例外を取得する場合は、マルチ スレッド環境で一括読み込みコンポーネントを実行しようとすると、:「インターフェイス SQLXMLBULKLOADLib.ISQLXMLBulkLoad の QueryInterface が失敗しました」。 回避策が、一括読み込みオブジェクト シングル スレッド アクセスを含むオブジェクトを作成するには (たとえばを使用して、 **[STAThread]**属性のサンプルで示すように)。  
  
 ここでは、データベースに XML データの一括読み込みを行う、実際の C# サンプル アプリケーションを紹介します。 実際のサンプルを作成するには、次の手順に従います。  
  
1.  次の表を作成します。  
  
    ```  
    CREATE TABLE Ord (  
             OrderID     int identity(1,1)  PRIMARY KEY,  
             CustomerID  varchar(5))  
    GO  
    CREATE TABLE Product (  
             ProductID   int identity(1,1) PRIMARY KEY,  
             ProductName varchar(20))  
    GO  
    CREATE TABLE OrderDetail (  
           OrderID     int FOREIGN KEY REFERENCES Ord(OrderID),  
           ProductID   int FOREIGN KEY REFERENCES Product(ProductID),  
                       CONSTRAINT OD_key PRIMARY KEY (OrderID, ProductID))  
    GO  
    ```  
  
2.  次のスキーマをファイル schema.xml に保存します。  
  
    ```  
    <xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
                xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
    <xsd:annotation>  
      <xsd:appinfo>  
        <sql:relationship name="OrderOD"  
              parent="Ord"  
              parent-key="OrderID"  
              child="OrderDetail"  
              child-key="OrderID" />  
  
        <sql:relationship name="ODProduct"  
              parent="OrderDetail"  
              parent-key="ProductID"  
              child="Product"  
              child-key="ProductID"   
              inverse="true"/>  
      </xsd:appinfo>  
    </xsd:annotation>  
  
      <xsd:element name="Order" sql:relation="Ord"   
                                sql:key-fields="OrderID" >  
       <xsd:complexType>  
         <xsd:sequence>  
            <xsd:element name="Product" sql:relation="Product"   
                         sql:key-fields="ProductID"  
                         sql:relationship="OrderOD ODProduct">  
              <xsd:complexType>  
                 <xsd:attribute name="ProductID" type="xsd:int" />  
                 <xsd:attribute name="ProductName" type="xsd:string" />  
              </xsd:complexType>  
            </xsd:element>  
         </xsd:sequence>  
            <xsd:attribute name="OrderID"   type="xsd:integer" />   
            <xsd:attribute name="CustomerID"   type="xsd:string" />  
        </xsd:complexType>  
      </xsd:element>  
    </xsd:schema>  
    ```  
  
3.  次のサンプル XML ドキュメントをファイル data.xml に保存します。  
  
    ```  
    <ROOT>    
      <Order OrderID="11" CustomerID="ALFKI">  
        <Product ProductID="11" ProductName="Chai" />  
        <Product ProductID="22" ProductName="Chang" />  
      </Order>  
      <Order OrderID="22" CustomerID="ANATR">  
         <Product ProductID="33" ProductName="Aniseed Syrup" />  
        <Product ProductID="44" ProductName="Gumbo Mix" />  
      </Order>  
    </ROOT>  
    ```  
  
4.  Visual Studio を起動します。  
  
5.  C# コンソール アプリケーションを作成します。  
  
6.  **プロジェクト**メニューの **参照の追加**です。  
  
7.  **COM**  タブで  **Microsoft SQLXML Bulkload 4.0 Type Library** (xblkld4.dll) をクリック**OK**です。 表示されます、 **Interop.SQLXMLBULKLOADLib**プロジェクトで作成されたアセンブリです。  
  
8.  Main() メソッドを次のコードに置き換え、 更新プログラム、 **ConnectionString**プロパティと、スキーマとデータ ファイルへのファイル パス。  
  
    ```  
    [STAThread]  
       static void Main(string[] args)  
       {     
             try  
             {  
                SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class objBL = new SQLXMLBULKLOADLib.SQLXMLBulkLoad4Class();  
                objBL.ConnectionString = "Provider=sqloledb;server=server;database=databaseName;integrated security=SSPI";  
                objBL.ErrorLogFile = "error.xml";  
                objBL.KeepIdentity = false;  
                objBL.Execute ("schema.xml","data.xml");  
             }  
             catch(Exception e)  
             {  
             Console.WriteLine(e.ToString());  
             }  
       }  
    ```  
  
9. 作成したテーブルに XML を読み込むには、プロジェクトをビルドして実行します。  
  
    > [!NOTE]  
    >  .NET Framework で提供される tlbimp.exe ツールを使用して、一括読み込みコンポーネント (xblkld4.dll) への参照を追加することもできます。 このツールでは、ネイティブ DLL (xblkld4.dll) のマネージ ラッパーが作成され、任意の .NET プロジェクトで使用できます。 例:  
  
    ```  
    c:\>tlbimp xblkld4.dll  
    ```  
  
     この例では、.NET Framework プロジェクトで使用できるマネージ ラッパー DLL (SQLXMLBULKLOADLib.dll) が作成されます。 新しく作成した DLL へのプロジェクト参照を、.NET Framework で追加します。  
  
## <a name="see-also"></a>参照  
 [XML データ &#40; の一括読み込みを実行します。SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)  
  
  
