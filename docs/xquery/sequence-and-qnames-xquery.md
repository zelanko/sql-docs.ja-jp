---
title: シーケンス名と Q 名 (XQuery) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- sequence [XQuery]
- XQuery, sequence
- QName [XQuery]
- predefined namespaces [XML in SQL Server]
ms.assetid: 3593ac26-dd78-4bf0-bb87-64fbcac5f026
author: rothja
ms.author: jroth
ms.openlocfilehash: c71a7139c3adb354923b3c953b367ab506f30545
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2020
ms.locfileid: "80380783"
---
# <a name="sequence-and-qnames-xquery"></a>シーケンスと QName (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  このトピックでは、XQuery の次の基本的な概念について説明します。  
  
-   Sequence  
  
-   QName と事前に定義された名前空間  
  
## <a name="sequence"></a>Sequence  
 XQuery では、式の結果は、XML ノードのリストと XSD アトミック型のインスタンスで構成されるシーケンスです。 シーケンス内の個々のエントリは、項目と呼ばれます。 シーケンス内のアイテムは、次のいずれかになります。  
  
-   要素、属性、テキスト、処理命令、コメント、ドキュメントなどのノード  
  
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
  
 前のクエリでは、`,``<step1>`構築の最後にあるコンマ ( ) がシーケンス コンストラクターであり、必須です。 結果の空白は説明用にのみ追加され、このドキュメントのすべての例の結果に含まれています。  
  
 シーケンスについて知っておくべき追加情報を次に示します。  
  
-   クエリの結果が他のシーケンスを含むシーケンスになる場合、含まれているシーケンスは外側のシーケンスにフラット化されます。 たとえば、シーケンス ((1,2, (3,4,5)),6) はデータ モデル内で (1, 2, 3, 4, 5, 6) にフラット化されます。  
  
    ```  
    DECLARE @x xml;  
    SET @x = '';  
    SELECT @x.query('(1,2, (3,4,5)),6');  
    ```  
  
-   空のシーケンスとは、アイテムが含まれていないシーケンスです。 これは「()」として表されます。  
  
-   1 つの項目のみを持つシーケンスは、アトミック値として扱うことができます。 すなわち、(1)=1である。  
  
 この実装では、シーケンスは同種でなければなりません。 つまり、アトミック値のシーケンスまたはノードのシーケンスのいずれかです。 たとえば、次の有効なシーケンスを示します。  
  
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
  
 次のクエリは、異種シーケンスがサポートされていないため、エラーを返します。  
  
```  
SELECT @x.query('<x>11</x>, 22');  
```  
  
## <a name="qname"></a>QName  
 XQuery の識別子は QName です。 QName は、名前空間プレフィックスとローカル名で構成されます。 この実装では、XQuery の変数名は QNames であり、接頭辞を持つことはできません。  
  
 型指定されていない**xml**変数に対してクエリを指定する次の例を考えてみます。  
  
```  
DECLARE @x xml;  
SET @x = '<Root><a>111</a></Root>';  
SELECT @x.query('/Root/a');  
```  
  
 式 (`/Root/a`) では、`Root` と `a` が QName です。  
  
 次の例では、型指定された**xml**列に対してクエリを指定します。 このクエリは、最初の\<ワークセンター位置にあるすべてのステップ>要素を反復処理します。  
  
```  
SELECT Instructions.query('  
   declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
for $Step in /AWMI:root/AWMI:Location[1]/AWMI:step  
      return  
           string($Step)   
') AS Result  
FROM Production.ProductModel  
WHERE ProductModelID=7;  
```  
  
 クエリ式では、次の点に注意してください。  
  
-   `AWMI root`、`AWMI:Location`、`AWMI:step`、`$Step` は、すべて QName です。 `AWMI`は、プレフィックス、 `root`、 `Location`、 `Step` 、およびすべてのローカル名です。  
  
-   変数`$step`は QName であり、接頭部はありません。  
  
 次の名前空間は、XQuery サポートで使用するために事前定義[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]されています。  
  
|Prefix|URI|  
|------------|---------|  
|xs|http://www.w3.org/2001/XMLSchema|  
|xsi|http://www.w3.org/2001/XMLSchema-instance|  
|xdt|http://www.w3.org/2004/07/xpath-datatypes|  
|fn|http://www.w3.org/2004/07/xpath-functions|  
|(プレフィックスなし)|`urn:schemas-microsoft-com:xml-sql`|  
|sql の種類|`https://schemas.microsoft.com/sqlserver/2004/sqltypes`|  
|xml|`http://www.w3.org/XML/1998/namespace`|  
|(プレフィックスなし)|`https://schemas.microsoft.com/sqlserver/2004/SOAP`|  
  
 作成するすべてのデータベースには **、sys** XML スキーマ コレクションがあります。 これらのスキーマは、ユーザーが作成した任意の XML スキーマ コレクションからアクセスできるように予約されます。  
  
> [!NOTE]  
>  この実装では、 の`local`XQuery 仕様で説明されているプレフィックスhttp://www.w3.org/2004/07/xquery-local-functionsはサポートされていません。  
  
## <a name="see-also"></a>関連項目  
 [XQuery の基礎](../xquery/xquery-basics.md)  
  
  
