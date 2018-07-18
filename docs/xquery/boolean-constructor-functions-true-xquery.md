---
title: true 関数 (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 08/10/2016
ms.prod: sql
ms.prod_service: sql
ms.component: xquery
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- fn:true function
- true function
ms.assetid: 318e370d-0444-4812-afe4-307df7ef9f3b
caps.latest.revision: 17
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 349b2f99f5db35ca9d44e3ac8459030b7f7ba55f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38014032"
---
# <a name="boolean-constructor-functions---true-xquery"></a>ブール値コンス トラクター関数 - true (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  xs:boolean 値 True を返します。 これは、`xs:boolean("1")` と同じです。  
  
## <a name="syntax"></a>構文  
  
```  
fn:true() as xs:boolean  
```  
  
## <a name="examples"></a>使用例  
 このトピックではさまざまなに格納されている XML インスタンスに対して XQuery の例について**xml**型の列には、AdventureWorks データベース。  
  
### <a name="a-using-the-true-xquery-boolean-function"></a>A. XQuery 論理関数 true() の使用  
 次の例は、型指定されていないクエリ**xml**変数。 内の式、 **value()** メソッドはブール値を返します**true()** "aaa"属性値である場合。 **Value()** のメソッド、 **xml**データ型がビットにブール値を変換し、それを返します。  
  
```  
DECLARE @x XML  
SET @x= '<ROOT><elem attr="aaa">bbb</elem></ROOT>'  
select @x.value(' if ( (/ROOT/elem/@attr)[1] eq "aaa" ) then fn:true() else fn:false() ', 'bit')  
go  
-- result = 1  
```  
  
 次の例では、クエリを指定する型指定されたに対して**xml**列。 `if`式の型指定されたブール値をチェックする、<`ROOT`> 要素を適宜構築済みの XML を返します。 この例では、次の操作が実行されます。  
  
-   定義する XML スキーマ コレクションを作成し、<`ROOT`> xs:boolean 型の要素。  
  
-   型指定されたテーブルを作成します。 **xml** XML スキーマ コレクションを使用して列。  
  
-   XML インスタンスを列に保存し、クエリを実行します。  
  
```  
-- Drop table if exist  
--DROP TABLE T  
--go  
DROP XML SCHEMA COLLECTION SC  
go  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
targetNamespace="QNameXSD" >  
      <element name="ROOT" type="boolean" nillable="true"/>  
</schema>'  
go  
CREATE TABLE T (xmlCol XML(SC))  
go  
-- following OK  
insert into T values ('<ROOT xmlns="QNameXSD">true</ROOT>')  
 go  
-- Retrieve the local name.   
SELECT xmlCol.query('declare namespace a="QNameXSD";   
   if (/a:ROOT[1] eq true()) then  
       <result>Found boolean true</result>  
   else  
       <result>Found boolean false</result>')  
  
FROM T  
-- result = <result>Found boolean true</result>  
-- Clean up  
DROP TABLE T  
go  
DROP XML SCHEMA COLLECTION SC  
go  
```  
  
## <a name="see-also"></a>参照  
 [ブール値コンス トラクター関数&#40;XQuery&#41;](http://msdn.microsoft.com/library/fa907f39-d4b7-4495-b829-c788928e0f64)  
  
  
