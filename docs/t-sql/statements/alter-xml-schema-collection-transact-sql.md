---
title: "ALTER XML SCHEMA COLLECTION (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_XML_SCHEMA_COLLECTION_TSQL
- ALTER XML SCHEMA COLLECTION
dev_langs:
- TSQL
helpviewer_keywords:
- schema collections [SQL Server], altering
- xml_schema_namespace function
- adding schema components
- ALTER XML SCHEMA COLLECTION statement
- XML schemas [SQL Server], adding
- XML schema collections [SQL Server], modifying
- schema collections [SQL Server], adding components
- XML schema collections [SQL Server], adding components
- importing schemas
- XML schema collections [SQL Server], altering
- schema collections [SQL Server], modifying
- multiple schema namespaces
ms.assetid: e311c425-742a-4b0d-b847-8b974bf66d53
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b33ecc2a5ca9838e5f9dd80dabd9bbddf90250ee
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="alter-xml-schema-collection-transact-sql"></a>ALTER XML SCHEMA COLLECTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存の XML スキーマ コレクションに新しいスキーマ コンポーネントを追加します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER XML SCHEMA COLLECTION [ relational_schema. ]sql_identifier ADD 'Schema Component'  
```  
  
## <a name="arguments"></a>引数  
 *relational_schema*  
 リレーショナル スキーマ名を指定します。 指定しない場合、既定のリレーショナル スキーマが使用されます。  
  
 *sql_identifier*  
 XML スキーマ コレクションの SQL 識別子を指定します。  
  
 **'** *スキーマ コンポーネント* **'**  
 挿入するスキーマ コンポーネントを指定します。  
  
## <a name="remarks"></a>解説  
 XML スキーマ コレクションにない名前空間を持つ XML スキーマを新しく追加する場合や、コレクションの既存の名前空間に新しいコンポーネントを追加する場合は、ALTER XML SCHEMA COLLECTION を使用します。  
  
 次の例は、新しく追加\<要素 > 既存の名前空間に`http://MySchema/test_xml_schema`コレクション内で`MyColl`です。  
  
```  
-- First create an XML schema collection.  
CREATE XML SCHEMA COLLECTION MyColl AS '  
   <schema   
    xmlns="http://www.w3.org/2001/XMLSchema"   
    targetNamespace="http://MySchema/test_xml_schema">  
      <element name="root" type="string"/>   
  </schema>'  
-- Modify the collection.   
ALTER XML SCHEMA COLLECTION MyColl ADD '  
  <schema xmlns="http://www.w3.org/2001/XMLSchema"   
         targetNamespace="http://MySchema/test_xml_schema">   
     <element name="anotherElement" type="byte"/>   
 </schema>';  
```  
  
 `ALTER XML SCHEMA`要素を追加`<anotherElement>`以前に定義された名前空間に`http://MySchema/test_xml_schema`です。  
  
 コレクション内に追加しようとしているコンポーネントの一部が、既に同じコレクション内にあるコンポーネントを参照している場合は、`<import namespace="referenced_component_namespace" />` を使用する必要があります。 ただし、`<xsd:import>` で現在のスキーマ名前空間を使用しても無効であり、現在のスキーマ名前空間と同じ名前空間からのコンポーネントは自動的にインポートされます。  
  
 コレクションを削除する使用[DROP XML SCHEMA COLLECTION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-xml-schema-collection-transact-sql.md).  
  
 スキーマ コレクションは既にには、lax 検証のワイルドカードまたは型の要素が含まれている場合**xs:anyType**、スキーマ コレクションに新しいグローバル要素、型、または属性の宣言を追加すると、すべての再検証、格納されています。スキーマ コレクションによって制約されているデータ。  
  
## <a name="permissions"></a>権限  
 XML SCHEMA COLLECTION を変更するには、コレクションに対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-xml-schema-collection-in-the-database"></a>A. データベースに XML スキーマ コレクションを作成する  
 次の例では、XML スキーマ コレクション `ManuInstructionsSchemaCollection` を作成します。 コレクションにはスキーマ名前空間が 1 つだけ含まれます。  
  
```  
-- Create a sample database in which to load the XML schema collection.  
CREATE DATABASE SampleDB;  
GO  
USE SampleDB;  
GO  
CREATE XML SCHEMA COLLECTION ManuInstructionsSchemaCollection AS  
N'<?xml version="1.0" encoding="UTF-16"?>  
<xsd:schema targetNamespace="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"   
   xmlns          ="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"   
   elementFormDefault="qualified"   
   attributeFormDefault="unqualified"  
   xmlns:xsd="http://www.w3.org/2001/XMLSchema" >  
  
    <xsd:complexType name="StepType" mixed="true" >  
        <xsd:choice  minOccurs="0" maxOccurs="unbounded" >   
            <xsd:element name="tool" type="xsd:string" />  
            <xsd:element name="material" type="xsd:string" />  
            <xsd:element name="blueprint" type="xsd:string" />  
            <xsd:element name="specs" type="xsd:string" />  
            <xsd:element name="diag" type="xsd:string" />  
        </xsd:choice>   
    </xsd:complexType>  
  
    <xsd:element  name="root">  
        <xsd:complexType mixed="true">  
            <xsd:sequence>  
                <xsd:element name="Location" minOccurs="1" maxOccurs="unbounded">  
                    <xsd:complexType mixed="true">  
                        <xsd:sequence>  
                            <xsd:element name="step" type="StepType" minOccurs="1" maxOccurs="unbounded" />  
                        </xsd:sequence>  
                        <xsd:attribute name="LocationID" type="xsd:integer" use="required"/>  
                        <xsd:attribute name="SetupHours" type="xsd:decimal" use="optional"/>  
                        <xsd:attribute name="MachineHours" type="xsd:decimal" use="optional"/>  
                        <xsd:attribute name="LaborHours" type="xsd:decimal" use="optional"/>  
                        <xsd:attribute name="LotSize" type="xsd:decimal" use="optional"/>  
                    </xsd:complexType>  
                </xsd:element>  
            </xsd:sequence>  
        </xsd:complexType>  
    </xsd:element>  
</xsd:schema>' ;  
GO  
-- Verify - list of collections in the database.  
SELECT *  
FROM sys.xml_schema_collections;  
-- Verify - list of namespaces in the database.  
SELECT name  
FROM sys.xml_schema_namespaces;  
  
-- Use it. Create a typed xml variable. Note the collection name   
-- that is specified.  
DECLARE @x xml (ManuInstructionsSchemaCollection);  
GO  
--Or create a typed xml column.  
CREATE TABLE T (  
        i int primary key,   
        x xml (ManuInstructionsSchemaCollection));  
GO  
-- Clean up.  
DROP TABLE T;  
GO  
DROP XML SCHEMA COLLECTION ManuInstructionsSchemaCollection;  
Go  
USE master;  
GO  
DROP DATABASE SampleDB;  
```  
  
 または、次のようにスキーマ コレクションを変数に割り当て、その変数を `CREATE XML SCHEMA COLLECTION` ステートメントで指定することもできます。  
  
```  
DECLARE @MySchemaCollection nvarchar(max);  
SET @MySchemaCollection  = N' copy the schema collection here';  
CREATE XML SCHEMA COLLECTION AS @MySchemaCollection;   
```  
  
 変数の例では`nvarchar(max)`型です。 変数を指定できますも**xml**場合は、それを文字列に変換が暗黙的に、データを入力します。  
  
 詳細については、「 [格納されている XML スキーマ コレクションの表示](../../relational-databases/xml/view-a-stored-xml-schema-collection.md)」を参照してください。  
  
 スキーマ コレクションを格納することができます、 **xml**型の列です。 この場合、XML スキーマ コレクションを作成するには、次の手順に従います。  
  
1.  SELECT ステートメントを使用して、列からスキーマ コレクションを取得しの変数に割り当てる**xml**型、または**varchar**型です。  
  
2.  CREATE XML SCHEMA COLLECTION ステートメントで変数名を指定します。  
  
 CREATE XML SCHEMA COLLECTION には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で認識されるスキーマ コンポーネントだけが格納されます。XML スキーマ内のすべての要素がデータベースに格納されるわけではありません。 したがって、XML スキーマ コレクションを、提供されたときと同じ状態に戻す場合は、データベース列またはコンピューター上の他のフォルダーに XML スキーマを保存することをお勧めします。  
  
### <a name="b-specifying-multiple-schema-namespaces-in-a-schema-collection"></a>B. スキーマ コレクションに複数のスキーマ名前空間を指定する  
 XML スキーマ コレクションを作成するときには、複数の XML スキーマを指定できます。 例:  
  
```  
CREATE XML SCHEMA COLLECTION N'  
<xsd:schema>....</xsd:schema>  
<xsd:schema>...</xsd:schema>';  
```  
  
 次の例は、XML スキーマ コレクションを作成`ProductDescriptionSchemaCollection`2 つの XML スキーマ名前空間が含まれます。  
  
```  
CREATE XML SCHEMA COLLECTION ProductDescriptionSchemaCollection AS   
'<xsd:schema targetNamespace="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"  
    xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"   
    elementFormDefault="qualified"   
    xmlns:xsd="http://www.w3.org/2001/XMLSchema" >  
    <xsd:element name="Warranty"  >  
        <xsd:complexType>  
            <xsd:sequence>  
                <xsd:element name="WarrantyPeriod" type="xsd:string"  />  
                <xsd:element name="Description" type="xsd:string"  />  
            </xsd:sequence>  
        </xsd:complexType>  
    </xsd:element>  
</xsd:schema>  
 <xs:schema targetNamespace="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription"   
    xmlns="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription"   
    elementFormDefault="qualified"   
    xmlns:mstns="http://tempuri.org/XMLSchema.xsd"   
    xmlns:xs="http://www.w3.org/2001/XMLSchema"  
    xmlns:wm="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain" >  
    <xs:import   
namespace="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain" />  
    <xs:element name="ProductDescription" type="ProductDescription" />  
        <xs:complexType name="ProductDescription">  
            <xs:sequence>  
                <xs:element name="Summary" type="Summary" minOccurs="0" />  
            </xs:sequence>  
            <xs:attribute name="ProductModelID" type="xs:string" />  
            <xs:attribute name="ProductModelName" type="xs:string" />  
        </xs:complexType>  
        <xs:complexType name="Summary" mixed="true" >  
            <xs:sequence>  
                <xs:any processContents="skip" namespace="http://www.w3.org/1999/xhtml" minOccurs="0" maxOccurs="unbounded" />  
            </xs:sequence>  
        </xs:complexType>  
</xs:schema>'  
;  
GO   
-- Clean up  
DROP XML SCHEMA COLLECTION ProductDescriptionSchemaCollection;  
GO  
```  
  
### <a name="c-importing-a-schema-that-does-not-specify-a-target-namespace"></a>C. 対象の名前空間が指定されていないスキーマをインポートする  
 含まれていないスキーマの場合は、 **targetNamespace**属性は、コレクションにインポートされて、そのコンポーネントは、次の例で示すように空の文字列のターゲットの名前空間に関連付けられています。 コレクションにインポートされる 1 つ以上のスキーマについて関連付けを行わない場合は、複数のスキーマ コンポーネント (場合によっては関係のないコンポーネント) が既定の空文字列の名前空間に関連付けられることになるため注意してください。  
  
```  
-- Create a collection that contains a schema with no target namespace.  
CREATE XML SCHEMA COLLECTION MySampleCollection AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  xmlns:ns="http://ns">  
<element name="e" type="dateTime"/>  
</schema>';  
GO  
-- query will return the names of all the collections that   
--contain a schema with no target namespace  
SELECT sys.xml_schema_collections.name   
FROM   sys.xml_schema_collections   
JOIN   sys.xml_schema_namespaces   
ON     sys.xml_schema_collections.xml_collection_id =   
       sys.xml_schema_namespaces.xml_collection_id   
WHERE  sys.xml_schema_namespaces.name='';  
```  
  
## <a name="see-also"></a>参照  
 [XML スキーマ コレクション &#40; を作成します。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)   
 [DROP XML SCHEMA COLLECTION &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-xml-schema-collection-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [型指定された XML と型指定されていない XML の比較](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [サーバー上の XML スキーマ コレクションの要件と制限](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
