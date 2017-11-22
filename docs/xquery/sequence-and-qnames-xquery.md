---
title: "シーケンスと Qname (XQuery) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- sequence [XQuery]
- XQuery, sequence
- QName [XQuery]
- predefined namespaces [XML in SQL Server]
ms.assetid: 3593ac26-dd78-4bf0-bb87-64fbcac5f026
caps.latest.revision: "22"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2414607a95b28aeba61bded3d9898ac25cb720a0
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="sequence-and-qnames-xquery"></a>シーケンスと QName (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  このトピックでは、次の XQuery の基本概念について説明します。  
  
-   Sequence  
  
-   QName と事前に定義された名前空間  
  
## <a name="sequence"></a>Sequence  
 XQuery では、式の結果は、XML ノードおよび XSD アトミック型のインスタンスの一覧で構成されるシーケンスです。 シーケンス内の個々のエントリはアイテムと呼ばれます。 シーケンス内のアイテムは、次のいずれかになります。  
  
-   要素、属性、テキスト、処理命令、コメント、またはドキュメントなどのノード  
  
-   XSD 単純型のインスタンスなどのアトミック値  
  
 たとえば、次のクエリでは、2 つの要素ノードのアイテムのシーケンスが作成されます。  
  
```  
SELECT Instructions.query('  
     <step1> Step 1 description goes here</step1>,  
     <step2> Step 2 description goes here </step2>  
') AS Result  
FROM Production.ProductModel  
WHERE ProductModelID=7;  
  
```  
  
 結果を次に示します。  
  
```  
<step1> Step 1 description goes here </step1>  
<step2> Step 2 description goes here </step2>   
```  
  
 上記のクエリでは、コンマ (`,`) の最後に、`<step1>`構築はシーケンス コンス トラクターであり、必要です。 結果に含まれる空白文字は説明の便宜上追加したもので、このドキュメント内のすべての例の結果にも同じ理由で空白文字を使用しています。  
  
 次に、シーケンスに関して理解する必要のある追加の情報を示します。  
  
-   クエリの結果が他のシーケンスを含むシーケンスになる場合、含まれているシーケンスは外側のシーケンスにフラット化されます。 たとえば、シーケンス ((1,2, (3,4,5)),6) はデータ モデル内で (1, 2, 3, 4, 5, 6) にフラット化されます。  
  
    ```  
    DECLARE @x xml;  
    SET @x = '';  
    SELECT @x.query('(1,2, (3,4,5)),6');  
    ```  
  
-   空のシーケンスとは、アイテムが含まれていないシーケンスです。 これは "()" で表されます。  
  
-   アイテムを 1 つしか持たないシーケンスは、アトミック値として扱うことができます。また、アトミック値は、1 つだけのアイテムを持つシーケンスとして扱うこともできます。 つまり (1) = 1 という式が成り立ちます。  
  
 この実装では、シーケンスは同種である必要があります。 つまり、アトミック値のシーケンスまたはノードのシーケンスのいずれかになります。 たとえば、有効なシーケンスは次のとおりです。  
  
```  
DECLARE @x xml;  
SET @x = '';  
-- Expression returns a sequence of 1 text node (singleton).  
SELECT @x.query('1');  
-- Expression returns a sequence of 2 text nodes  
SELECT @x.query('"abc", "xyz"');  
-- Expression returns a sequence of one atomic value. data() returns  
-- typed value of the node.  
SELECT @x.query('data(1)');  
-- Expression returns a sequence of one element node.   
-- In the expression XML construction is used to construct an element.  
SELECT @x.query('<x> {1+2} </x>');  
```  
  
 異種シーケンスはサポートされていないため、次のクエリはエラーを返します。  
  
```  
SELECT @x.query('<x>11</x>, 22');  
```  
  
## <a name="qname"></a>QName  
 XQuery の識別子は QName です。 QName は、名前空間プレフィックスとローカル名で構成されます。 この実装では、XQuery の変数名は QName であり、プレフィックスは付きません。  
  
 クエリが指定されている次の例を検討してください、型指定されていないに対して**xml**変数。  
  
```  
DECLARE @x xml;  
SET @x = '<Root><a>111</a></Root>';  
SELECT @x.query('/Root/a');  
```  
  
 式 (`/Root/a`) では、`Root` と `a` が QName です。  
  
 次の例では、クエリが指定されて、型指定されたに対して**xml**列です。 クエリの反復すべて\<手順 > 最初のワーク センターからの場所にある要素。  
  
```  
SELECT Instructions.query('  
   declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
for $Step in /AWMI:root/AWMI:Location[1]/AWMI:step  
      return  
           string($Step)   
') AS Result  
FROM Production.ProductModel  
WHERE ProductModelID=7;  
```  
  
 クエリ式では、次の点に注意してください。  
  
-   `AWMI root`、`AWMI:Location`、`AWMI:step`、`$Step` は、すべて QName です。 `AWMI`プレフィックスであり、 `root`、`Location`と`Step`はすべてのローカル名。  
  
-   `$step`変数は QName であり、プレフィックスはありません。  
  
 次の名前空間は XQuery サポートで使用する定義済み[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]です。  
  
|プレフィックス|[URI]|  
|------------|---------|  
|xs|http://www.w3.org/2001/XMLSchema|  
|xsi|http://www.w3.org/2001/XMLSchema-instance|  
|xdt|http://www.w3.org/2004/07/xpath-datatypes|  
|fn|http://www.w3.org/2004/07/xpath-functions|  
|(プレフィックスなし)|`urn:schemas-microsoft-com:xml-sql`|  
|sqltypes|http://schemas.microsoft.com/sqlserver/2004/sqltypes|  
|xml|`http://www.w3.org/XML/1998/namespace`|  
|(プレフィックスなし)|`http://schemas.microsoft.com/sqlserver/2004/SOAP`|  
  
 各データベースを作成するには、 **sys** XML スキーマ コレクションです。 各データベースにはこれらのスキーマが保持されるため、ユーザーが作成した XML スキーマ コレクションからアクセスすることができます。  
  
> [!NOTE]  
>  この実装では、http://www.w3.org/2004/07/xquery-local-functions の XQuery 仕様に記載されている `local` プレフィックスはサポートされません。  
  
## <a name="see-also"></a>参照  
 [XQuery の基礎](../xquery/xquery-basics.md)  
  
  
