---
title: Sequence と QNames (XQuery) |Microsoft Docs
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
ms.openlocfilehash: fbb20c9e14c4e76b8862a23e8d758fcbba94da7f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67946345"
---
# <a name="sequence-and-qnames-xquery"></a>シーケンスと QName (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  このトピックでは、XQuery の次の基本的な概念について説明します。  
  
-   Sequence  
  
-   QName と事前に定義された名前空間  
  
## <a name="sequence"></a>Sequence  
 XQuery では、式の結果は、XML ノードのリストと XSD アトミック型のインスタンスで構成されるシーケンスになります。 シーケンス内の個々のエントリは、項目と呼ばれます。 シーケンス内のアイテムは、次のいずれかになります。  
  
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
  
 前のクエリでは、`,` `<step1>`構築の最後にあるコンマ () はシーケンスコンストラクターであり、必須です。 結果の空白は、説明のためだけに追加されており、このドキュメントのすべての例の結果に含まれています。  
  
 シーケンスについて理解しておく必要がある追加情報を次に示します。  
  
-   クエリの結果が他のシーケンスを含むシーケンスになる場合、含まれているシーケンスは外側のシーケンスにフラット化されます。 たとえば、シーケンス ((1,2, (3,4,5)),6) はデータ モデル内で (1, 2, 3, 4, 5, 6) にフラット化されます。  
  
    ```  
    DECLARE @x xml;  
    SET @x = '';  
    SELECT @x.query('(1,2, (3,4,5)),6');  
    ```  
  
-   空のシーケンスとは、アイテムが含まれていないシーケンスです。 これは "()" として表されます。  
  
-   1つの項目のみを含むシーケンスはアトミック値として処理できます。また、その逆も可能です。 つまり、(1) = 1 です。  
  
 この実装では、シーケンスは同種である必要があります。 つまり、一連のアトミック値またはノードのシーケンスがあるとします。 たとえば、有効なシーケンスは次のとおりです。  
  
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
  
 異種シーケンスはサポートされていないため、次のクエリではエラーが返されます。  
  
```  
SELECT @x.query('<x>11</x>, 22');  
```  
  
## <a name="qname"></a>QName  
 XQuery の識別子は QName です。 QName は、名前空間プレフィックスとローカル名で構成されます。 この実装では、XQuery の変数名は Qname であり、プレフィックスを持つことはできません。  
  
 型指定されていない**xml**変数に対してクエリを指定する次の例を考えてみます。  
  
```  
DECLARE @x xml;  
SET @x = '<Root><a>111</a></Root>';  
SELECT @x.query('/Root/a');  
```  
  
 式 (`/Root/a`) では、`Root` と `a` が QName です。  
  
 次の例では、型指定された**xml**列に対してクエリが指定されています。 クエリは、最初の\<ワークセンターの場所にあるすべてのステップ> 要素を反復処理します。  
  
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
  
-   
  `AWMI root`、`AWMI:Location`、`AWMI:step`、`$Step` は、すべて QName です。 `AWMI`はプレフィックスであり、 `root`、 `Location`、および`Step`はすべてローカル名です。  
  
-   `$step`変数は QName であり、プレフィックスを持っていません。  
  
 次の名前空間は、の[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]XQuery サポートで使用するために事前に定義されています。  
  
|Prefix|URI|  
|------------|---------|  
|xs|http://www.w3.org/2001/XMLSchema|  
|xsi|http://www.w3.org/2001/XMLSchema-instance|  
|xdt|http://www.w3.org/2004/07/xpath-datatypes|  
|fn|http://www.w3.org/2004/07/xpath-functions|  
|(プレフィックスなし)|`urn:schemas-microsoft-com:xml-sql`|  
|sqltypes|https://schemas.microsoft.com/sqlserver/2004/sqltypes|  
|xml|`http://www.w3.org/XML/1998/namespace`|  
|(プレフィックスなし)|`https://schemas.microsoft.com/sqlserver/2004/SOAP`|  
  
 作成するすべてのデータベースには、 **sys** XML スキーマコレクションがあります。 これらのスキーマは、ユーザーが作成した XML スキーマコレクションからアクセスできるように予約されています。  
  
> [!NOTE]  
>  この実装では、の`local` http://www.w3.org/2004/07/xquery-local-functionsXQuery 仕様で説明されているように、プレフィックスはサポートされません。  
  
## <a name="see-also"></a>参照  
 [XQuery の基礎](../xquery/xquery-basics.md)  
  
  
