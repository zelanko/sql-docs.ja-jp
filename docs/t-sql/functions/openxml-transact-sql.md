---
title: "OPENXML (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPENXML_TSQL
- OPENXML
dev_langs: TSQL
helpviewer_keywords:
- OPENXML statement
- rowsets [SQL Server], XML documents
- XML [SQL Server], rowset views
ms.assetid: 8088b114-7d01-435a-8e0d-b81abacc86d6
caps.latest.revision: "24"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f5b32c99393bb5b7f31423df840f7f0069dd3518
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="openxml-transact-sql"></a>OPENXML (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  XML ドキュメントに対して行セット ビューを提供します。 OPENXML を使用することができます OPENXML は行セット プロバイダーであるため、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントが行セット内のテーブル、ビュー、または OPENROWSET 関数などのプロバイダーを表示できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
OPENXML( idoc int [ in] , rowpattern nvarchar [ in ] , [ flags byte [ in ] ] )   
[ WITH ( SchemaDeclaration | TableName ) ]  
```  
  
## <a name="arguments"></a>引数  
 *idoc*  
 XML ドキュメントの内部表現のドキュメント ハンドルを指定します。 呼び出して XML ドキュメントの内部表現が作成された**sp_xml_preparedocument**です。  
  
 *rowpattern*  
 ノードを識別するために使用する XPath パターン (ハンドルが渡された XML ドキュメントで、 *idoc*パラメーター) 行として処理されるためです。  
  
 *flags*  
 XML データとリレーショナル行セットとの間で使用するマッピング、およびオーバーフローした列の処理方法を指定します。 *フラグ*オプションの入力パラメーターは、次の値のいずれかになります。  
  
|バイト値|Description|  
|----------------|-----------------|  
|**0**|既定値は**属性中心**マッピングします。|  
|**1**|使用して、**属性中心**マッピングします。 XML_ELEMENTS と組み合わせることができます。 この場合、**属性中心**マッピングは、最初に適用し、**要素中心**でまだ処理されていないすべての列のマッピングが適用されます。|  
|**2**|使用して、**要素中心**マッピングします。 XML_ATTRIBUTES と組み合わせることができます。 ここでは、**属性中心**マッピングは、最初に適用し、**要素中心**処理されていないすべての列のマッピングが適用されます。|  
|**8**|XML_ATTRIBUTES または XML_ELEMENTS と組み合わせる (論理和) ことができます。 このフラグがオーバーフロー プロパティを使用したデータをコピーしないことを示すコンテキストでは、取得できるように、  **@mp:xmltext**です。|  
  
 *SchemaDeclaration*  
 フォームのスキーマ定義です: *ColName * * ColType* [*ColPattern* | *メタプロパティ*] [**、* * *ColNameColType* [*ColPattern * |*メタプロパティ*]...]  
  
 *ColName*  
 行セット内の列名を指定します。  
  
 *ColType*  
 行セット内の列の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型を指定します。 基になると、列の型が異なる場合**xml**属性、強制型変換のデータ型が発生します。  
  
 *ColPattern*  
 XML ノードを列へマップする方法を表す標準 XPath パターンを指定します (省略可能)。 場合*ColPattern*が指定されていない、既定のマッピング (**属性中心**または**要素中心**で指定されたマッピング*フラグ*) 行われます。  
  
 として指定した XPath パターン*ColPattern*マッピングの特別な性質の指定に使用される (の場合、**属性中心**と**要素中心**マッピング) します。上書きまたは拡張によって示される既定のマッピング*フラグ*です。  
  
 として指定する標準 XPath パターン*ColPattern*メタプロパティもサポートします。  
  
 *MetaProperty*  
 OPENXML で提供されるメタプロパティの 1 つを指定します。 場合*メタプロパティ*が指定されている列には、メタプロパティで提供される情報が含まれています。 これらのメタプロパティによって、XML ノードの情報 (相対的な位置や名前空間の情報など) を抽出でき、 これにより、テキストとして表示されている情報だけでなく、さらに多くの情報を取得することができます。  
  
 *TableName*  
 テーブル名を指定できます (の代わりに*SchemaDeclaration*) 目的のスキーマを持つテーブルが既に存在し、列パターンが必要ないかどうか。  
  
## <a name="remarks"></a>解説  
 WITH 句は、いずれかを使用して行セットの形式 (および必要に応じて、追加のマッピング情報) を提供*SchemaDeclaration* 、既存の指定または*TableName*です。 句を使用して、オプションが指定されていない場合、結果が返されます、**エッジ**テーブル形式です。 エッジ テーブルでは、1 つのテーブル内での詳細な XML ドキュメントの構造 (要素/属性名、ドキュメント階層、名前空間、PI など) が表されます。  
  
 次の表の構造、**エッジ**テーブル。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**id**|**bigint**|ドキュメント ノードの一意の ID。<br /><br /> ルート要素には、ID 値 0 があります。 負の ID 値は予約済みです。|  
|**parentid**|**bigint**|ノードの親の識別子。 この ID によって識別される親のノードは、必ずしも要素ではなく、この ID によって親が識別されるノードの NodeType に依存します。 たとえば、ノードがテキスト ノードである場合、その親は属性ノードである場合もあります。<br /><br /> ノードが XML ドキュメントの最上位にある場合、その **ParentID** は NULL になります。|  
|**nodetype**|**int**|ノードの型の識別子。 XML DOM ノードの型番号に対応する整数です。<br /><br /> ノードの型は次のとおりです。<br /><br /> 1 = 要素ノード<br /><br /> 2 = 属性ノード<br /><br /> 3 = テキスト ノード|  
|**localname**|**nvarchar**|要素または属性のローカル名。 DOM オブジェクトに名前がない場合は NULL になります。|  
|**プレフィックス**|**nvarchar**|ノード名の名前空間のプレフィックス。|  
|**namespaceuri**|**nvarchar**|ノードの名前空間 URI。 値が NULL の場合、名前空間はありません。|  
|**datatype**|**nvarchar**|要素または属性行の実際のデータ型。それ以外の行は NULL になります。 データ型は、インライン DTD またはインライン スキーマから推定されます。|  
|**prev**|**bigint**|前の兄弟要素の XML ID。 前に直接の兄弟がない場合は NULL になります。|  
|**text**|**ntext**|属性の値またはテキスト形式での要素の内容が含まれています (場合は NULL、**エッジ**テーブル エントリの値は必要ありません)。|  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-a-simple-select-statement-with-openxml"></a>A. OPENXML と共に単純な SELECT ステートメントを使用する  
 次の例では、`sp_xml_preparedocument` を使用して XML イメージの内部表現を作成します。 次に、XML ドキュメントの内部表現に対して、`SELECT` 行セット プロバイダーを使用して `OPENXML` ステートメントを実行します。  
  
 *フラグ*に値が設定されている`1`です。 これを示します**属性中心**マッピングします。 したがって、XML 属性は行セット内の列にマップされます。 *Rowpattern*として指定された`/ROOT/Customer`を識別、`<Customers>`処理するノードをします。  
  
 省略可能な*ColPattern*列名には、XML 属性の名前が一致するので、(列パターン) パラメーターが指定されていません。  
  
 `OPENXML` 行セット プロバイダーでは、2 列の行セット (`CustomerID` および `ContactName`) が作成されます。`SELECT` ステートメントでは、これらの行セットから必要な列 (この場合はすべての列) を取得します。  
  
```  
DECLARE @idoc int, @doc varchar(1000);  
SET @doc ='  
<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order CustomerID="VINET" EmployeeID="5" OrderDate="1996-07-04T00:00:00">  
      <OrderDetail OrderID="10248" ProductID="11" Quantity="12"/>  
      <OrderDetail OrderID="10248" ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order CustomerID="LILAS" EmployeeID="3" OrderDate="1996-08-16T00:00:00">  
      <OrderDetail OrderID="10283" ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>';  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @idoc OUTPUT, @doc;  
-- Execute a SELECT statement that uses the OPENXML rowset provider.  
SELECT    *  
FROM       OPENXML (@idoc, '/ROOT/Customer',1)  
            WITH (CustomerID  varchar(10),  
                  ContactName varchar(20));  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
CustomerID ContactName            
---------- --------------------   
VINET      Paul Henriot  
LILAS      Carlos Gonzlez  
```  
  
 場合同じ`SELECT`ステートメントを実行すると*フラグ*'éý'`2`を示す、**要素中心**の値をマップします`CustomerID`と`ContactName`の両方に、。という名前の要素がないため、XML ドキュメント内の顧客は、NULL として返されます`CustomerID`または`ContactName`XML ドキュメントにします。  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
CustomerID ContactName  
---------- -----------  
NULL       NULL  
NULL       NULL  
```  
  
### <a name="b-specifying-colpattern-for-mapping-between-columns-and-the-xml-attributes"></a>B. 列と XML 属性の間のマッピングに ColPattern を指定する  
 次のクエリでは、XML ドキュメントから顧客 ID、注文日、製品 ID、および数量の属性を返します。 *Rowpattern*を識別、`<OrderDetails>`要素。 `ProductID` および `Quantity` は、`<OrderDetails>` 要素の属性です。 ただし、`OrderID`、`CustomerID`、および `OrderDate` は、親要素 (`<Orders>`) の属性です。  
  
 省略可能な*ColPattern*を指定します。 これは、次のことを示します。  
  
-   `OrderID`、 `CustomerID`、および`OrderDate`で識別されるノードの親の属性を行セットのマップで*rowpattern* XML ドキュメントにします。  
  
-   `ProdID`行セット内の列にマップされて、`ProductID`属性、および`Qty`行セット内の列にマップされて、`Quantity`で識別されたノードの属性*rowpattern*です。  
  
 ただし、**要素中心**マッピングを指定、*フラグ*パラメーターで指定したマッピング*ColPattern*このマッピングが上書きされます。  
  
```  
DECLARE @idoc int, @doc varchar(1000);   
SET @doc ='  
<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order OrderID="10248" CustomerID="VINET" EmployeeID="5"   
           OrderDate="1996-07-04T00:00:00">  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">v  
   <Order OrderID="10283" CustomerID="LILAS" EmployeeID="3"   
           OrderDate="1996-08-16T00:00:00">  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>';   
  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @idoc OUTPUT, @doc;   
  
-- SELECT stmt using OPENXML rowset provider  
SELECT *  
FROM   OPENXML (@idoc, '/ROOT/Customer/Order/OrderDetail',2)   
         WITH (OrderID       int         '../@OrderID',   
               CustomerID  varchar(10) '../@CustomerID',   
               OrderDate   datetime    '../@OrderDate',   
               ProdID      int         '@ProductID',   
               Qty         int         '@Quantity');  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
OrderID CustomerID           OrderDate                 ProdID    Qty  
------------------------------------------------------------------------  
10248      VINET       1996-07-04 00:00:00.000   11      12  
10248      VINET       1996-07-04 00:00:00.000   42      10  
10283      LILAS       1996-08-16 00:00:00.000   72      3  
```  
  
### <a name="c-obtaining-results-in-an-edge-table-format"></a>C. エッジ テーブル形式で結果を取得する  
 次の例では、サンプルの XML ドキュメントから成る`<Customers>`、 `<Orders>`、および`<Order_0020_Details>`要素。 最初に、 **sp_xml_preparedocument**ドキュメント ハンドルを取得するために呼び出されます。 このドキュメント ハンドルに渡される`OPENXML`です。  
  
 `OPENXML`ステートメント、 *rowpattern* (`/ROOT/Customers`) を識別、`<Customers>`処理するノードです。 WITH 句が指定されていないため`OPENXML`で行セットを返します、**エッジ**テーブル形式です。  
  
 最後に、`SELECT`ステートメント内のすべての列を取得、**エッジ**テーブル。  
  
```  
DECLARE @idoc int, @doc varchar(1000);   
SET @doc ='  
<ROOT>  
<Customers CustomerID="VINET" ContactName="Paul Henriot">  
   <Orders CustomerID="VINET" EmployeeID="5" OrderDate=  
           "1996-07-04T00:00:00">  
      <Order_x0020_Details OrderID="10248" ProductID="11" Quantity="12"/>  
      <Order_x0020_Details OrderID="10248" ProductID="42" Quantity="10"/>  
   </Orders>  
</Customers>  
<Customers CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Orders CustomerID="LILAS" EmployeeID="3" OrderDate=  
           "1996-08-16T00:00:00">  
      <Order_x0020_Details OrderID="10283" ProductID="72" Quantity="3"/>  
   </Orders>  
</Customers>  
</ROOT>';  
  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @idoc OUTPUT, @doc;   
  
-- SELECT statement that uses the OPENXML rowset provider.  
SELECT    *  
FROM       OPENXML (@idoc, '/ROOT/Customers')   
EXEC sp_xml_removedocument @idoc;  
  
```  
  
## <a name="see-also"></a>参照  
 [例: OPENXML の使用](../../relational-databases/xml/examples-using-openxml.md)  
  
  
