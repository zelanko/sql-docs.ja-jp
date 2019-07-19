---
title: 一次式 (XQuery) |Microsoft Docs
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
- variable references [XQuery]
- primary expressions [XQuery]
- function calls [XQuery]
- expressions [XQuery], primary
- literals [XQuery]
- context item expressions [XQuery]
ms.assetid: d4183c3e-12b5-4ca0-8413-edb0230cb159
author: rothja
ms.author: jroth
ms.openlocfilehash: e8704a01d810477fd0359196cb622984da357cf6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67946388"
---
# <a name="primary-expressions-xquery"></a>原始式 (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  XQuery 原始式には、リテラル、変数参照、コンテキスト アイテム式、コンス トラクター、および関数呼び出しが含まれます。  
  
## <a name="literals"></a>リテラル  
 XQuery リテラルには、数値型または文字列型のリテラルを使用できます。 文字列リテラルには、定義済みのエンティティ参照を含めることができます。エンティティ参照は文字のシーケンスです。 シーケンスは、構文上意味を持つことも考えられる 1 文字を表すアンパサンドで始まります。 XQuery の定義済みエンティティ参照を次に示します。  
  
|エンティティ参照|表す内容|  
|----------------------|----------------|  
|&lt;|\<|  
|&gt;|>|  
|&amp;|&|  
|&quot;|"|  
|&apos;|'|  
  
 文字列リテラルには、10 進または 16 進のコード ポイントで識別される文字参照 (Unicode 文字への XML 形式の参照) を含めることもできます。 たとえば、文字参照でユーロの通貨記号を表すことができます"&\#8364;"します。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、XML Version 1.0 が解析の基準として使用されます。  
  
### <a name="examples"></a>使用例  
 リテラル、エンティティ参照、および文字参照の使用方法を次の例に示します。  
  
 '`<'` 文字、および `'>`' 文字には特別な意味があるため、このコードはエラーを返します。  
  
```  
DECLARE @var XML  
SET @var = ''  
SELECT @var.query(' <SalaryRange>Salary > 50000 and < 100000</SalaryRange>')  
GO  
```  
  
 代わりにエンティティ参照を使用すると、このクエリは動作します。  
  
```  
DECLARE @var XML  
SET @var = ''  
SELECT @var.query(' <SalaryRange>Salary > 50000 and < 100000</SalaryRange>')  
GO  
```  
  
 文字参照を使用してユーロの通貨記号を表す方法を次の例に示します。  
  
```  
DECLARE @var XML  
SET @var = ''  
SELECT @var.query(' <a>€12.50</a>')  
```  
  
 結果は次のとおりです。  
  
 `<a>€12.50</a>`  
  
 次の例では、クエリをアポストロフィで区切っています。 この場合、文字列値のアポストロフィは隣接した 2 つのアポストロフィで表されます。  
  
```  
DECLARE @var XML  
SET @var = ''  
SELECT @var.query('<a>I don''t know</a>')  
Go  
```  
  
 結果は次のとおりです。  
  
 `<a>I don't know</a>`  
  
 組み込みの Boolean 関数**true()** と**false()** 、ブール値を表す次の例に示すように使用できます。  
  
```  
DECLARE @var XML  
SET @var = ''  
SELECT @var.query('<a>{true()}</a>')  
GO  
```  
  
 直接要素コンストラクターにより、式が中かっこ内に指定されています。 結果の XML では、式の結果値で置き換えられます。  
  
 結果は次のとおりです。  
  
 `<a>true</a>`  
  
## <a name="variable-references"></a>変数参照  
 XQuery 内の変数参照は前にドル記号 ($) が付いた QName で表されます。 この実装では、プレフィックスのない変数参照だけがサポートされます。 たとえば、次のクエリでは、変数 `$i` は FLWOR 式の中で定義されています。  
  
```  
DECLARE @var XML  
SET @var = '<root>1</root>'  
SELECT @var.query('  
 for $i in /root return data($i)')  
GO  
```  
  
 次のクエリは、変数名に名前空間プレフィックスが加えられているため動作しません。  
  
```  
DECLARE @var XML  
SET @var = '<root>1</root>'  
SELECT @var.query('  
DECLARE namespace x="https://X";  
for $x:i in /root return data($x:i)')  
GO  
```  
  
 次のクエリで示すように、SQL 変数を参照する sql:variable() 拡張関数を使用できます。  
  
```  
DECLARE @price money  
SET @price=2500  
DECLARE @x xml  
SET @x = ''  
SELECT @x.query('<value>{sql:variable("@price") }</value>')  
```  
  
 結果は次のとおりです。  
  
 `<value>2500</value>`  
  
#### <a name="implementation-limitations"></a>実装の制限事項  
 次に、実装の制限事項を示します。  
  
-   名前空間プレフィックス付きの変数はサポートされていません。  
  
-   モジュールのインポートはサポートされていません。  
  
-   外部変数の宣言はサポートされていません。 これに対する解決策は、使用する、 [sql:variable() 関数](../xquery/xquery-extension-functions-sql-variable.md)します。  
  
## <a name="context-item-expressions"></a>コンテキスト アイテム式  
 コンテキスト アイテムは、パス式のコンテキストで現在処理中のアイテムです。 コンテキスト アイテムが NULL ではない XML データ型インスタンス内にある場合は、ドキュメント ノードで初期化されます。 Nodes() メソッド、XPath 式のコンテキストまたは述語で変更することもできます。  
  
 コンテキスト アイテムはドット (.) を含む式によって返されます。 たとえば、次のクエリでは、各 <`a`> 要素について `attr` 属性が存在するかどうかを評価します。 attr 属性が存在する場合は、その要素が返されます。 述語の中の条件は、コンテキスト ノードが 1 つのピリオドで指定されていることを示しています。  
  
```  
DECLARE @var XML  
SET @var = '<ROOT>  
<a>1</a>  
<a attr="1">2</a>  
</ROOT>'  
SELECT @var.query('/ROOT[1]/a[./@attr]')  
```  
  
 結果は次のとおりです。  
  
 `<a attr="1">2</a>`  
  
## <a name="function-calls"></a>関数の呼び出し  
 組み込みの XQuery 関数を呼び出すことができます、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sql:variable() と sql:column() 関数。 実装済み関数の一覧は、次を参照してください。 [xml データ型に対する XQuery 関数](../xquery/xquery-functions-against-the-xml-data-type.md)します。  
  
#### <a name="implementation-limitations"></a>実装の制限事項  
 次に、実装の制限事項を示します。  
  
-   XQuery プロローグでの関数定義はサポートされていません。  
  
-   関数のインポートはサポートされていません。  
  
## <a name="see-also"></a>参照  
 [XML の構築&#40;XQuery&#41;](../xquery/xml-construction-xquery.md)  
  
  
