---
title: "XPath データ型 (SQLXML 4.0) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- mapping XDR types to XPath types [SQLXML]
- data types [XPath]
- arithmetic operators
- mapping data types [SQLXML]
- relational operators [SQLXML]
- node-set [SQLXML]
- data types [SQLXML], XPath
- XPath operators [SQLXML]
- XDR data type [SQLXML]
- equality operators [SQLXML]
- XPath conversions [SQLXML]
- converting data types [SQLXML]
- Boolean operators
- XPath queries [SQLXML], data types
- XPath data types [SQLXML]
- operators [SQLXML]
ms.assetid: a90374bf-406f-4384-ba81-59478017db68
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d36d141e552750650ede74ba2aba92b203825558
ms.sourcegitcommit: 37f0b59e648251be673389fa486b0a984ce22c81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2018
---
# <a name="xpath-data-types-sqlxml-40"></a>XPath のデータ型 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、XPath、および XML Schema (XSD) のデータ型は大きく異なります。 たとえば、XPath に整数や日付のデータ型はありませんが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と XSD にはこれらのデータ型が多く用意されています。 また、XSD では時間値の精度はナノ秒ですが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の精度は最大でも 1/300 秒です。 このため、あるデータ型から別のデータ型へのマッピングが常に可能であるとは限りません。 マッピングの詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]XSD データ型へのデータ型を参照してください[データ型の強制変換と sql:datatype 注釈 &#40;です。SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).  
  
 XPath が 3 つのデータ型:**文字列**、**数**、および**ブール**です。 **数**データ型は、IEEE 754 倍精度浮動小数点では常にします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Float (53)**データ型は XPath に最も近い**数**です。 ただし、 **float (53)** IEEE 754 では正確に一致しません。 たとえば、非数 (NaN) も無限大も使用されません。 数値以外の文字列を変換しようとしています。**数**エラー 0 個の結果で除算しようとします。  
  
## <a name="xpath-conversions"></a>XPath 変換  
 `OrderDetail[@UnitPrice > "10.0"]` などの XPath クエリを使用する場合は、データ型の変換を暗黙的に行うか明示的に行うかによって、クエリの意味が微妙に変わります。 このため、XPath データ型の実装方法について理解しておくことが重要です。 XPath 言語仕様 "XML Path Language (XPath) version 1.0 W3C Proposed Recommendation 8 October 1999" は、W3C Web サイト (http://www.w3.org/TR/1999/PR-xpath-19991008.html) で参照できます。  
  
 XPath の演算子は、次の 4 つのカテゴリに分けられます。  
  
-   論理演算子 (and、or)  
  
-   関係演算子 (\<、>、 \<=、> =)  
  
-   等価演算子 (=、!=)  
  
-   算術演算子 (+、-、*、div、mod)  
  
 各カテゴリの演算子では、それぞれ異なる方法で各自のオペランドが変換されます。 XPath の演算子では、必要に応じて各自のオペランドが暗黙的に変換されます。 算術演算子のオペランドが変換**数**、および数値の結果。 ブール演算子はオペランドを変換**ブール**、およびブール値の結果。 関係演算子と等価演算子では、ブール値が得られます。 ただし、次の表に示すように、オペランドの変換元のデータ型に応じて、それぞれ異なる変換規則が使用されます。  
  
|オペランド|関係演算子|等値演算子|  
|-------------|-------------------------|-----------------------|  
|両方のオペランドがノード セットの場合|TRUE の場合にだけ、1 つのセット内のノードがあるし、2 番目のノード セットのようなその比較、**文字列**値は TRUE です。|同じ。|  
|ノード セットを他の 1 つは、**文字列**です。|ノード セット内のノードがある場合にのみ TRUE になるように変換すると**数**での比較、**文字列**に変換**数**true を指定します。|ノード セット内のノードがある場合にのみ TRUE になるように変換すると**文字列**での比較、**文字列**true を指定します。|  
|ノード セットを他の 1 つは、**数**です。|ノード セット内のノードがある場合にのみ TRUE になるように変換すると**数**での比較、**数**true を指定します。|同じ。|  
|ノード セットを他の 1 つは、**ブール**です。|ノード セット内のノードがある場合にのみ TRUE になるように変換される**ブール**し**数**での比較、**ブール**に変換**数**true を指定します。|ノード セット内のノードがある場合にのみ TRUE になるように変換すると**ブール**での比較、**ブール**true を指定します。|  
|どちらもノード セットでない場合|両方のオペランドを変換**数**し比較。|両方のオペランドを共通のデータ型に変換し比較。 変換**ブール**いずれかの場合**ブール**、**数**いずれかの場合**数**、それ以外の変換**文字列**.|  
  
> [!NOTE]  
>  XPath の関係演算子はオペランドが常に変換ため**数**、**文字列**比較はできません。 日付の比較を含めるには、するは、SQL Server 2000 は、このバリエーションを XPath 仕様を提供しています: 関係演算子を比較すると、**文字列**を**文字列**、ノード セットと、**文字列**、または、文字列値ノード セットに、文字列値ノード セット、**文字列**比較 (されません、**数**比較) を実行します。  
  
## <a name="node-set-conversions"></a>ノード セット変換  
 ノード セット変換は常に直感的なものとは限りません。 ノード セットに変換されます、**文字列**によってセット内の最初のノードだけの文字列値を取得します。 ノード セットに変換されます**数**に変換することで**文字列**、変換して**文字列**に**数**です。 ノード セットに変換されます**ブール**その存在をテストしています。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ノード セットで位置の選択を実行しない: たとえば、XPath クエリ`Customer[3]`3 番目の顧客の位置の選択には、この型はサポートされていません。 つまり[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 そのため、ノード-設定-を-**文字列**またはノード-設定-に-**数**ように、XPath 仕様で説明されている変換が実装されていません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、XPath 仕様で "先頭" の意味で指定されているものが "任意" の意味として扱われます。 たとえば、XPath クエリは、W3C XPath 仕様に基づいて`Order[OrderDetail/@UnitPrice > 10.0]`注文が 1 つ選択**OrderDetail**を持つ、 **UnitPrice** 10.0 を超える。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この XPath クエリは、いずれかと、それらの注文を選択します**OrderDetail**を持つ、 **UnitPrice** 10.0 を超える。  
  
 変換**ブール**、存在検査が生成されますテストです。 したがって、XPath クエリ`Products[@Discontinued=true()]`が SQL 式と同じ"Products.Discontinued is not null"の場合、SQL 式ではない"Products.Discontinued = 1" です。 クエリを後者の SQL 式に相当するためには、最初に変換されたノード セット以外**ブール**など、入力**数**です。 たとえば、 `Products[number(@Discontinued) = true()]`のようにします。  
  
 大半の演算子は、ノード セット内の 1 つ以上のノードに対して TRUE であれば TRUE となるように定義されているので、これらの演算はノード セットが空の場合は常に FALSE となります。 したがって、A が空の場合、`A = B` と `A != B` は両方とも FALSE になり、`not(A=B)` と `not(A!=B)` は TRUE になります。  
  
 通常、属性または列にマップされる要素が存在するデータベース内の列の値がない場合**null**です。 行にマップされる要素は、子が存在する場合に存在します。  
  
> [!NOTE]  
>  注釈される要素**定数**は常に存在します。 したがって、XPath 述語で使用できません**が定数**要素。  
  
 ノード セットが変換される場合**文字列**または**数**その XDR 型 (存在する場合) は、注釈付きスキーマで検証、およびその型は必要な変換が判別に使用します。  
  
## <a name="mapping-xdr-data-types-to-xpath-data-types"></a>XDR データ型から XPath データ型へのマッピング  
 次の表に示すようにノードの XPath データ型は、スキーマ内の XDR データ型から派生した (ノード**EmployeeID**説明の目的に使用)。  
  
|XDR データ型|同等の<br /><br /> XPath データ型|使用される SQL Server 変換|  
|-------------------|------------------------------------|--------------------------------|  
|Nonebin.base64bin.hex|なし|NoneEmployeeID|  
|boolean|boolean|CONVERT(bit, EmployeeID)|  
|number、int、float,i1、i2、i4、i8、r4、r8ui1、ui2、ui4、ui8|number|CONVERT(float(53), EmployeeID)|  
|id、idref、idrefsentity、entities、enumerationnotation、nmtoken、nmtokens、chardate、Timedate、Time.tz、string、uri、uuid|string|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|fixed14.4|N/A (XDR データ型 fixed14.4 に相当する XPath のデータ型はありません)|CONVERT(money, EmployeeID)|  
|date|string|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|time<br /><br /> time.tz|string|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
 日付と時刻の変換は、データベースを使用して、値が格納されているかどうかを使用するように設計されています、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime**データ型または**文字列**です。 なお、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime**データの種類を使用しません**タイム ゾーン**XML より小さい有効桁数と**時間**データ型。 含める、**タイムゾーン**内のデータを格納しているデータ型または追加の有効桁数[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して、**文字列**型です。  
  
 ノードが XDR データ型から XPath データ型に変換される場合は、1 つの XPath データ型から別の XPath データ型へ、追加の変換が必要になることがあります。 たとえば、次の XPath クエリを考えてみます。  
  
```  
(@m + 3) = 4  
```  
  
 場合@mは、 **fixed14.4** XDR データ型、XDR データ型から XPath データ型が使用されるへの変換。  
  
```  
CONVERT(money, m)  
```  
  
 この変換では、ノードで`m`から変換された**fixed14.4**に**money**です。 しかし、値 3 を加算するには追加の変換が必要になります。  
  
```  
CONVERT(float(CONVERT(money, m))  
```  
  
 この XPath 式は、次のように評価されます。  
  
```  
CONVERT(float(CONVERT(money, m)) + CONVERT(float(53), 3) = CONVERT(float(53), 3)  
```  
  
 次の表に示すように、これは、リテラルや複合式など、他の XPath 式に適用される変換と同じです。  
  
||||||  
|-|-|-|-|-|  
||X が不明|X is **string**|X は**数**|X は**ブール**|  
|string(X)|CONVERT (nvarchar(4000), X, 126)|-|CONVERT (nvarchar(4000), X, 126)|CASE WHEN X THEN N'true' ELSE N'false' END|  
|number(X)|CONVERT (float(53), X)|CONVERT (float(53), X)|-|CASE WHEN X THEN 1 ELSE 0 END|  
|boolean(X)|-|LEN(X) > 0|X != 0|-|  
  
## <a name="examples"></a>使用例  
  
### <a name="a-convert-a-data-type-in-an-xpath-query"></a>A. XPath クエリ内のデータ型を変換する  
 注釈付き XSD スキーマに対して指定された次の XPath クエリで選択するクエリをすべて**従業員**を持つノード、 **EmployeeID** E-1、ここで"e-"は、プレフィックスを使用して指定の値の属性、**sql:id-プレフィックス**注釈。  
  
 `Employee[@EmployeeID="E-1"]`  
  
 クエリ内の述語は、次の SQL 式と等価です。  
  
 `N'E-' + CONVERT(nvarchar(4000), Employees.EmployeeID, 126) = N'E-1'`  
  
 **EmployeeID**の 1 つ、 **id** (**idref**、 **idrefs**、 **nmtoken**、 **nmtokens**など)、XSD スキーマでのデータ型値**EmployeeID**に変換されます、**文字列**前に説明した変換規則を使用して XPath データ型。  
  
 `CONVERT(nvarchar(4000), Employees.EmployeeID, 126)`  
  
 文字列に "E-" プレフィックスが追加され、結果が `N'E-1'` と比較されます。  
  
### <a name="b-perform-several-data-type-conversions-in-an-xpath-query"></a>B. XPath クエリ内で複数のデータ型変換を実行する  
 注釈付き XSD スキーマに対して指定される XPath クエリ `OrderDetail[@UnitPrice * @OrderQty > 98]` を考えてみます。  
  
 この XPath クエリでは、すべてを返します、  **\<OrderDetail >** 、述語を満たす要素`@UnitPrice * @OrderQty > 98`です。 場合、 **UnitPrice**注釈が付いて、 **fixed14.4**データ型の注釈付きスキーマでは、この述語は SQL 式に相当します。  
  
 `CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice)) * CONVERT(float(53), OrderDetail.OrderQty) > CONVERT(float(53), 98)`  
  
 XPath クエリ内の値を変換するとき、最初の変換では、XDR データ型を XPath データ型に変換します。 XSD データ型ため**UnitPrice**は**fixed14.4**、前の表のように、これは、使用される最初の変換。  
  
```  
CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 算術演算子のオペランドを変換するため、**数**XPath データ型の 1 つの XPath データ型から別の XPath データ型に) 2 番目の変換が適用される値に変換が**float (53)** (**float (53)**に近い XPath は**数**データ型)。  
  
```  
CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 仮定した場合、 **OrderQty** XSD データ型を持たない属性**OrderQty**に変換されますが、**数**1 回の変換での XPath データ型。  
  
```  
CONVERT(float(53), OrderDetail.OrderQty)  
```  
  
 同様に、98 は変換後の値を**数**XPath データ型。  
  
```  
CONVERT(float(53), 98)  
```  
  
> [!NOTE]  
>  スキーマで使用されている XSD データ型は、基になると互換性がない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、データベースのデータ型または不可能の XPath データ型の変換が実行される、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラーを返す可能性があります。 たとえば場合、 **EmployeeID**属性の注釈が付いて**id プレフィックス**注釈、XPath`Employee[@EmployeeID=1]`ためエラーが発生**EmployeeID**が、**id プレフィックス**注釈に変換できないと**数**です。  
  
  
