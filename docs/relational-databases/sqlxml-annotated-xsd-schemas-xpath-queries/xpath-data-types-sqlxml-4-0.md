---
title: XPath データ型 (SQLXML 4.0) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
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
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c9f66bf1ded94b0877309917e9f03e71512ac8f0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68051591"
---
# <a name="xpath-data-types-sqlxml-40"></a>XPath のデータ型 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、XPath、および XML Schema (XSD) のデータ型は大きく異なります。 たとえば、XPath に整数や日付のデータ型はありませんが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と XSD にはこれらのデータ型が多く用意されています。 また、XSD では時間値の精度はナノ秒ですが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の精度は最大でも 1/300 秒です。 このため、あるデータ型から別のデータ型へのマッピングが常に可能であるとは限りません。 マッピングの詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、XSD データ型にデータ型を参照してください[データ型の強制変換、sql:datatype 注釈&#40;SQLXML 4.0&#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)。  
  
 XPath が 3 つのデータ型:**文字列**、**数**、および**ブール**します。 **数**データ型は、IEEE 754 倍精度浮動小数点では常にします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Float (53)** データ型が XPath に最も近い**数**します。 ただし、 **float (53)** IEEE 754 ではありません。 たとえば、非数 (NaN) も無限大も使用されません。 数値以外の文字列を変換しようとしています。**数**エラー 0 個の結果で除算しようとします。  
  
## <a name="xpath-conversions"></a>XPath 変換  
 `OrderDetail[@UnitPrice > "10.0"]` などの XPath クエリを使用する場合は、データ型の変換を暗黙的に行うか明示的に行うかによって、クエリの意味が微妙に変わります。 このため、XPath データ型の実装方法について理解しておくことが重要です。 XML パス言語 (XPath) version 1.0 W3C XPath 言語仕様の W3C Web サイトで 8 1999 年 10 月の推奨事項を提示するを参照して http://www.w3.org/TR/1999/PR-xpath-19991008.html 。  
  
 XPath の演算子は、次の 4 つのカテゴリに分けられます。  
  
-   論理演算子 (and、or)  
  
-   関係演算子 (\<、>、 \<=、> =)  
  
-   等価演算子 (=、!=)  
  
-   算術演算子 (+、-、*、div、mod)  
  
 各カテゴリの演算子では、それぞれ異なる方法で各自のオペランドが変換されます。 XPath の演算子では、必要に応じて各自のオペランドが暗黙的に変換されます。 算術演算子の変換はオペランドが**数**、され、数値が得られます。 ブール演算子はオペランドを変換**ブール**、され、ブール値が得られます。 関係演算子と等価演算子では、ブール値が得られます。 ただし、次の表に示すように、オペランドの変換元のデータ型に応じて、それぞれ異なる変換規則が使用されます。  
  
|オペランド|関係演算子|等値演算子|  
|-------------|-------------------------|-----------------------|  
|両方のオペランドがノード セットの場合|TRUE の場合にのみセットを 1 つのノードがあるし、2 番目のノード セットなどその比較、**文字列**値は TRUE になります。|同じ。|  
|1 つは、他のノードのセットを**文字列**します。|ノード セット内のノードがある場合にのみ TRUE されるように変換される**数**での比較、**文字列**に変換**数**は TRUE です。|ノード セット内のノードがある場合にのみ TRUE されるように変換される**文字列**での比較、**文字列**は TRUE です。|  
|1 つは、他のノードのセットを**数**します。|ノード セット内のノードがある場合にのみ TRUE されるように変換される**数**での比較、**数**は TRUE です。|同じ。|  
|1 つは、他のノードのセットを**ブール**します。|ノード セット内のノードがある場合にのみ TRUE されるように変換される**ブール**し**数**での比較、**ブール**に変換**数**は TRUE です。|ノード セット内のノードがある場合にのみ TRUE されるように変換される**ブール**での比較、**ブール**は TRUE です。|  
|どちらもノード セットでない場合|両方のオペランドを変換**数**し比較。|両方のオペランドを共通のデータ型に変換し比較。 変換**ブール**いずれかの場合**ブール**、**数**いずれかの場合**数**それ以外に変換**文字列**。|  
  
> [!NOTE]  
>  XPath の関係演算子はオペランドを常に変換するため、**数**、**文字列**比較はできません。 日付の比較を含めるには、SQL Server 2000 は、XPath 仕様にこのバリエーションの 1 つを提供します。関係演算子を比較すると、**文字列**を**文字列**、ノード セットと、**文字列**、または、文字列値ノード セットを文字列値ノード セットを**文字列**比較 (いない、**数**比較) が実行されます。  
  
## <a name="node-set-conversions"></a>ノード セット変換  
 ノード セット変換は常に直感的なものとは限りません。 ノード セットに変換されます、**文字列**セット内の最初のノードのみの文字列値を取得しています。 ノード セットに変換されます**数**に変換してから、**文字列**、および変換し、**文字列**に**数**します。 ノード セットに変換されます**ブール**によってその存在をテストします。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ノード セットで位置の選択は実行されません。たとえば、XPath クエリ `Customer[3]` は 3 番目の顧客を意味しますが、このような位置の選択は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではサポートされていません。 ノードではそのため、-設定-に-**文字列**またはノードの設定-に-**数**XPath 仕様での説明に従って、変換は実装されていません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、XPath 仕様で "先頭" の意味で指定されているものが "任意" の意味として扱われます。 W3C XPath 仕様に XPath クエリに基づいて、たとえば、 `Order[OrderDetail/@UnitPrice > 10.0]` 、最初にそれらの注文を選択**OrderDetail**は、 **[単価]** 10.0 よりも大きい。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、次の XPath クエリでこれらの注文を選択する**OrderDetail**は、 **[単価]** 10.0 よりも大きい。  
  
 変換**ブール**、存在検査が生成されますテスト。 したがって、XPath クエリ`Products[@Discontinued=true()]`が SQL 式と同じ"products.discontinued is null でない"、SQL 式ではありません"Products.Discontinued = 1" です。 クエリを後者の SQL 式に相当するためには、以外を最初にノード セットを変換**ブール**などの入力**数**します。 たとえば、`Products[number(@Discontinued) = true()]` のようにします。  
  
 大半の演算子は、ノード セット内の 1 つ以上のノードに対して TRUE であれば TRUE となるように定義されているので、これらの演算はノード セットが空の場合は常に FALSE となります。 したがって、A が空の場合、`A = B` と `A != B` は両方とも FALSE になり、`not(A=B)` と `not(A!=B)` は TRUE になります。  
  
 通常、属性または列にマップされる要素が存在するデータベース内の列の値がない場合**null**します。 行にマップされる要素は、子が存在する場合に存在します。  
  
> [!NOTE]  
>  要素の注釈が付けられた**は定数**常に存在します。 したがって、XPath 述語で使用できません**は定数**要素。  
  
 ノード セットに変換するときに**文字列**または**数**(ある場合) は、その XDR 型は、注釈付きスキーマで検証、および、その型に必要な変換が判別に使用されます。  
  
## <a name="mapping-xdr-data-types-to-xpath-data-types"></a>XDR データ型から XPath データ型へのマッピング  
 次の表に示すように、ノードの XPath データ型は、スキーマ内の XDR データ型から派生した (ノード **[社員コード]** は、例示の目的に使用)。  
  
|XDR データ型|同等の表記<br /><br /> XPath データ型|使用される SQL Server 変換|  
|-------------------|------------------------------------|--------------------------------|  
|Nonebin.base64bin.hex|なし|NoneEmployeeID|  
|boolean|boolean|CONVERT(bit, EmployeeID)|  
|number、int、float,i1、i2、i4、i8、r4、r8ui1、ui2、ui4、ui8|number|CONVERT(float(53), EmployeeID)|  
|id、idref、idrefsentity、entities、enumerationnotation、nmtoken、nmtokens、chardate、Timedate、Time.tz、string、uri、uuid|string|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|fixed14.4|N/A (XDR データ型 fixed14.4 に相当する XPath のデータ型はありません)|CONVERT(money, EmployeeID)|  
|日付|string|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|time<br /><br /> time.tz|string|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
 日付と時刻の変換はデータベースを使用して、値が格納されているかどうかを使用するように設計、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime**データ型または**文字列**します。 なお、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime**データ型を使用しません**タイムゾーン**XML よりも小さい有効桁数と**時間**データ型。 含める、**タイムゾーン**内のデータを格納しているデータ型または追加の有効桁数[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して、**文字列**型。  
  
 ノードが XDR データ型から XPath データ型に変換される場合は、1 つの XPath データ型から別の XPath データ型へ、追加の変換が必要になることがあります。 たとえば、次の XPath クエリを考えてみます。  
  
```  
(@m + 3) = 4  
```  
  
 場合@mは、 **fixed14.4** XDR データ型、XDR データ型から XPath データ型には、使用への変換。  
  
```  
CONVERT(money, m)  
```  
  
 この変換では、ノードで`m`から変換**fixed14.4**に**money**します。 しかし、値 3 を加算するには追加の変換が必要になります。  
  
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
||X が不明|X は**文字列**|X は**数**|X は**ブール**|  
|string(X)|CONVERT (nvarchar(4000), X, 126)|-|CONVERT (nvarchar(4000), X, 126)|CASE WHEN X THEN N'true' ELSE N'false' END|  
|number(X)|CONVERT (float(53), X)|CONVERT (float(53), X)|-|CASE WHEN X THEN 1 ELSE 0 END|  
|boolean(X)|-|LEN(X) > 0|X != 0|-|  
  
## <a name="examples"></a>使用例  
  
### <a name="a-convert-a-data-type-in-an-xpath-query"></a>A. XPath クエリ内のデータ型を変換する  
 注釈付き XSD スキーマに対して指定された次の XPath クエリでクエリが選択すべて**従業員**ノードを**EmployeeID**属性の値が E-1 で"e-"が指定されるプレフィックスの**sql:id-プレフィックス**注釈。  
  
 `Employee[@EmployeeID="E-1"]`  
  
 クエリ内の述語は、次の SQL 式と等価です。  
  
 `N'E-' + CONVERT(nvarchar(4000), Employees.EmployeeID, 126) = N'E-1'`  
  
 **[社員コード]** の 1 つ、 **id** (**idref**、 **idrefs**、 **nmtoken**、 **nmtokens**というように)、XSD スキーマのデータ型の値 **[社員コード]** に変換され、**文字列**前に説明した変換規則を使用して、XPath のデータ型。  
  
 `CONVERT(nvarchar(4000), Employees.EmployeeID, 126)`  
  
 文字列に "E-" プレフィックスが追加され、結果が `N'E-1'` と比較されます。  
  
### <a name="b-perform-several-data-type-conversions-in-an-xpath-query"></a>B. XPath クエリ内で複数のデータ型変換を実行する  
 注釈付き XSD スキーマに対して指定される XPath クエリ `OrderDetail[@UnitPrice * @OrderQty > 98]` を考えてみます。  
  
 次の XPath クエリが返すすべての **\<OrderDetail >** 、述語を満たす要素`@UnitPrice * @OrderQty > 98`。 場合、 **UnitPrice**で注釈が、 **fixed14.4**データ型の注釈付きスキーマでは、この述語は SQL 式と同じです。  
  
 `CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice)) * CONVERT(float(53), OrderDetail.OrderQty) > CONVERT(float(53), 98)`  
  
 XPath クエリ内の値を変換するとき、最初の変換では、XDR データ型を XPath データ型に変換します。 XSD データ型であるため**UnitPrice**は**fixed14.4**、ために使用される最初の変換で、前の表のように、これは。  
  
```  
CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 算術演算子にオペランドを変換するため、**数**XPath データ型から XPath データ型別の XPath データ型から) の 2 番目の変換が適用されるに値を変換する**float(53)** (**float(53)** 、XPath には、**数**データ型)。  
  
```  
CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 仮定すると、 **OrderQty** XSD データ型を持たない属性**OrderQty**に変換されます、**数**1 回の変換での XPath データ型。  
  
```  
CONVERT(float(53), OrderDetail.OrderQty)  
```  
  
 同様に、値 98 に変換されます、**数**XPath データ型。  
  
```  
CONVERT(float(53), 98)  
```  
  
> [!NOTE]  
>  スキーマで使用されている XSD データ型は、基になるとは互換性がない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、データベース内のデータ型または変換を実行することは不可能の XPath データ型の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラーが返される場合があります。 などの場合、 **[社員コード]** 属性は、注釈が付けられた**id プレフィックス**アノテーションでは、XPath`Employee[@EmployeeID=1]`エラーが生成されますので **[社員コード]** は、**id プレフィックス**アノテーションに変換することはできませんと**数**。  
  
  
