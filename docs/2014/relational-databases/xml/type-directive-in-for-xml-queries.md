---
title: FOR XML クエリの TYPE ディレクティブ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: xml
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, TYPE directive
- TYPE directive
ms.assetid: a3df6c30-1f25-45dc-b5a9-bd0e41921293
caps.latest.revision: 40
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d331e0a22042258c087a3f58b0c72330c66f9203
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "43889418"
---
# <a name="type-directive-in-for-xml-queries"></a>FOR XML クエリの TYPE ディレクティブ
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サポート、 [xml &#40;TRANSACT-SQL&#41; ](/sql/t-sql/xml/xml-transact-sql) FOR XML クエリの結果として返す要求オプションには、 `xml` TYPE ディレクティブを指定することによってデータ型。 これにより、サーバーで FOR XML クエリの結果を処理できるようになります。 たとえば、それに対して XQuery を指定に結果を割り当てる、`xml`変数、または書き込み[入れ子になった FOR XML クエリ](use-nested-for-xml-queries.md)します。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] TYPE ディレクティブを使用した FOR XML クエリなど、または XML データ型のインスタンス データを別のサーバー構成の結果としてクライアントに返します、`xml`から SQL テーブルの列と出力 XML インスタンス データ値を返すデータ型が使用されますパラメーター。 クライアント アプリケーション コードでは、ADO.NET プロバイダーが、この XML データ型の情報をサーバーからバイナリ エンコードで送信するように要求します。 ただし、TYPE ディレクティブを指定せずに FOR XML を使用した場合、この XML データは文字列型として返されます。 どんな場合でも、クライアント プロバイダーは常にいずれかの形式の XML を処理できます。 TYPE ディレクティブを指定していない最上位レベルでの FOR XML 句は、カーソルと共に使用できません。  
  
## <a name="examples"></a>使用例  
 次の例は、FOR XML クエリでの TYPE ディレクトリの使用方法を示しています。  
  
### <a name="retrieving-for-xml-query-results-as-xml-type"></a>FOR XML クエリの結果の xml 型としての取得  
 次のクエリでは、 `Contacts` テーブルから顧客の連絡先に関する情報を取得します。 `TYPE` に `FOR XML` ディレクティブが指定されているので、結果は `xml` 型として返されます。  
  
```  
USE AdventureWorks2012;  
Go  
SELECT BusinessEntityID, FirstName, LastName  
FROM Person.Person  
ORDER BY BusinessEntityID  
FOR XML AUTO, TYPE;  
```  
  
 結果の一部を次に示します。  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="Sánchez"/>`  
  
 `<Person.Person BusinessEntityID="2" FirstName="Terri" LastName="Duffy"/>`  
  
 `...`  
  
### <a name="assigning-for-xml-query-results-to-an-xml-type-variable"></a>FOR XML クエリ結果の xml 型の変数への代入  
 次の例では、FOR XML の結果が割り当てられている、`xml`型の変数、`@x`します。 クエリなど、連絡先情報を取得します、 `BusinessEntityID`、 `FirstName`、 `LastName`、およびその他からの電話番号、`AdditionalContactInfo`の列`xml``TYPE`します。 `FOR XML` 句に `TYPE` ディレクティブを指定するので、この XML は `xml` 型として返され、変数に代入されます。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @x xml;  
SET @x = (  
   SELECT BusinessEntityID,   
          FirstName,   
          LastName,   
          AdditionalContactInfo.query('  
declare namespace aci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
              //act:telephoneNumber/act:number') as MorePhoneNumbers  
   FROM Person.Person  
   FOR XML AUTO, TYPE);  
SELECT @x;  
GO  
```  
  
### <a name="querying-results-of-a-for-xml-query"></a>FOR XML クエリの結果のクエリ  
 FOR XML クエリにより、XML が返されます。 そのため、適用`xml`など、メソッドの入力`query()`と`value()`、FOR XML クエリによって返された XML 結果にします。  
  
 次のクエリで、`query()`のメソッド、`xml`データ型を使用すると、クエリの結果、`FOR XML`クエリ。 詳細については、「[クエリ&#40;&#41; メソッド &#40;xml データ型&#41;](/sql/t-sql/xml/query-method-xml-data-type)」を参照してください。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT (SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
DECLARE namespace aci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
DECLARE namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
 //act:telephoneNumber/act:number  
') AS PhoneNumbers  
FROM Person.Person  
FOR XML AUTO, TYPE).query('/Person.Person[1]');  
```  
  
 内部`SELECT … FOR XML`のクエリを返します、`xml`する結果を入力、外部`SELECT`適用、`query()`メソッドを`xml`型。 `TYPE` ディレクティブが指定されていることに注意してください。  
  
 結果を次に示します。  
  
 `<Person.Person BusinessEntityID="1" FirstName="Ken" LastName="Sánchez">`  
  
 `<PhoneNumbers>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">111-111-1111</act:number>`  
  
 `<act:number xmlns:act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes">112-111-1111</act:number>`  
  
 `</PhoneNumbers>`  
  
 `</Person.Person>`  
  
 次のクエリでは、`xml` データ型の `value()` メソッドを使用して、`SELECT…FOR XML` クエリにより返された XML 結果から値を取得します。 詳細については、「[value&#40;&#41; メソッド &#40;xml データ型&#41;](/sql/t-sql/xml/value-method-xml-data-type)」を参照してください。  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @FirstPhoneFromAdditionalContactInfo varchar(40);  
SELECT @FirstPhoneFromAdditionalContactInfo =   
 ( SELECT BusinessEntityID, FirstName, LastName, AdditionalContactInfo.query('  
declare namespace aci="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactInfo";  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
   //act:telephoneNumber/act:number  
   ') AS PhoneNumbers  
   FROM Person.Person Contact  
   FOR XML AUTO, TYPE).value('  
declare namespace act="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ContactTypes";  
  /Contact[@BusinessEntityID="1"][1]/PhoneNumbers[1]/act:number[1]', 'varchar(40)'  
 )  
SELECT @FirstPhoneFromAdditionalContactInfo;  
```  
  
 `value()` メソッドの XQuery パス式により、 `BusinessEntityID` が `1`の顧客の連絡先から 1 つ目の電話番号が取得されます。  
  
> [!NOTE]  
>  FOR XML クエリの結果を型として返される場合は、TYPE ディレクティブが指定されていない`nvarchar(max)`します。  
  
### <a name="using-for-xml-query-results-in-insert-update-and-delete-transact-sql-dml"></a>INSERT、UPDATE、および DELETE (Transact-SQL DML) での FOR XML クエリの結果の使用  
 次の例では、FOR XML クエリをデータ操作言語 (DML) ステートメントで使用する方法について説明します。 この例で、`FOR XML`のインスタンスを返します`xml`型。 また、 `INSERT` ステートメントによりこの XML がテーブルに挿入されます。  
  
```  
CREATE TABLE T1(intCol int, XmlCol xml);  
GO  
INSERT INTO T1   
VALUES(1, '<Root><ProductDescription ProductModelID="1" /></Root>');  
GO  
  
CREATE TABLE T2(XmlCol xml)  
GO  
INSERT INTO T2(XmlCol)   
SELECT (SELECT XmlCol.query('/Root')   
        FROM T1   
        FOR XML AUTO,TYPE);   
GO  
```  
  
## <a name="see-also"></a>参照  
 [FOR XML &#40;SQL Server&#41;](../xml/for-xml-sql-server.md)  
  
  
