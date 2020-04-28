---
title: ローカル名-QName (XQuery) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:local-name-from-QName function
- local-name-from-QName function
ms.assetid: fafed718-8c3c-403f-93ee-ec51fc157a6e
author: rothja
ms.author: jroth
ms.openlocfilehash: 765d412b9f3f0395a9bca6fd52c74135ddde3ff4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68004562"
---
# <a name="functions-related-to-qnames---local-name-from-qname"></a>QNames に関係する関数 - local-name-from-QName
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  *$Arg*によって指定された QName のローカル部分を表す XS: NCNAME を返します。 *$Arg*が空のシーケンスの場合、結果は空のシーケンスになります。  
  
## <a name="syntax"></a>構文  
  
```  
fn:local-name-from-QName($arg as xs:QName?) as xs:NCName?  
```  
  
## <a name="arguments"></a>引数  
 *$arg*  
 ローカル名部分を抽出する QName です。  
  
## <a name="examples"></a>使用例  
 このトピックでは、 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]データベースのさまざまな**xml**型の列に格納されている xml インスタンスに対して XQuery の例を示します。  
  
 次の例では、**ローカル名-qname ()** 関数を使用して、qname 型の値からローカル名と名前空間 URI の部分を取得します。 この例では、次の処理を実行します。  
  
-   XML スキーマコレクションを作成します。  
  
-   xml 型の列を持つテーブルの作成。 Xml 型は、XML スキーマコレクションを使用して型指定されます。  
  
-   サンプル XML インスタンスをテーブルに格納します。 Xml データ型の**query ()** メソッドを使用すると、クエリ式を実行して、インスタンスから QName 型の値のローカル名部分を取得します。  
  
```sql
DROP TABLE T  
go  
DROP XML SCHEMA COLLECTION SC  
go  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
targetNamespace="QNameXSD" >  
      <element name="root" type="QName" nillable="true"/>  
</schema>'  
go  
  
CREATE TABLE T (xmlCol XML(SC))  
go  
-- following OK  
insert into T values ('<root xmlns="QNameXSD" xmlns:a="https://someURI">a:someLocalName</root>')  
 go  
-- Retrieve the local name.   
SELECT xmlCol.query('declare default element namespace "QNameXSD"; local-name-from-QName(/root[1])')  
FROM T  
-- Result = someLocalName  
-- You can retrieve namespace URI part from the QName using the namespace-uri-from-QName() function  
SELECT xmlCol.query('declare default element namespace "QNameXSD"; namespace-uri-from-QName(/root[1])')  
FROM T  
-- Result = https://someURI  
```  
  
## <a name="see-also"></a>参照  
 [QNames &#40;XQuery&#41;に関連する関数](https://msdn.microsoft.com/library/7e07eb26-f551-4b63-ab77-861684faff71)  
  
  
