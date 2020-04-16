---
title: データ型 (SQLXML)
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
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 089b2b006d0159c63e480c8627762ac37dec98b8
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "75247086"
---
# <a name="xpath-data-types-sqlxml-40"></a>XPath のデータ型 (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、XPath、および XML スキーマ (XSD) のデータ型は非常に異なります。 たとえば、XPath に整数や日付のデータ型はありませんが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と XSD にはこれらのデータ型が多く用意されています。 また、XSD では時間値の精度はナノ秒ですが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の精度は最大でも 1/300 秒です。 このため、あるデータ型から別のデータ型へのマッピングが常に可能であるとは限りません。 データ型を XSD[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型にマップする方法の詳細については、「[データ型の強制変換」および sqlXML 4.0&#41;&#40;sql:datatype アノテーション](../../relational-databases/sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)を参照してください。  
  
 XPath には、**文字列**、**数値**、**およびブール**型の 3 つのデータ型があります。 **数値**データ型は、常に IEEE 754 倍精度浮動小数点です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **float(53)** データ型は XPath 番号に最も近い**値です**。 ただし **、float(53) は**正確には IEEE 754 ではありません。 たとえば、非数 (NaN) も無限大も使用されません。 数値以外の文字列を**数値**に変換しようとして、0 で除算しようとすると、エラーになります。  
  
## <a name="xpath-conversions"></a>XPath 変換  
 `OrderDetail[@UnitPrice > "10.0"]` などの XPath クエリを使用する場合は、データ型の変換を暗黙的に行うか明示的に行うかによって、クエリの意味が微妙に変わります。 このため、XPath データ型の実装方法について理解しておくことが重要です。 XPath 言語仕様の XML パス言語 (XPath) バージョン 1.0 W3C 提案勧告 1999 年 10http://www.w3.org/TR/1999/PR-xpath-19991008.html月 8 日は、W3C の Web サイトで確認できます。  
  
 XPath の演算子は、次の 4 つのカテゴリに分けられます。  
  
-   論理演算子 (and、or)  
  
-   関係演算子\<( , \<>, =, >= )  
  
-   等価演算子 (=、!=)  
  
-   算術演算子 (+、-、*、div、mod)  
  
 各カテゴリの演算子では、それぞれ異なる方法で各自のオペランドが変換されます。 XPath の演算子では、必要に応じて各自のオペランドが暗黙的に変換されます。 算術演算子は、オペランドを**number**に変換し、結果として数値を返します。 ブール演算子はオペランドを**ブール型**に変換し、結果としてブール値を返します。 関係演算子と等価演算子では、ブール値が得られます。 ただし、次の表に示すように、オペランドの変換元のデータ型に応じて、それぞれ異なる変換規則が使用されます。  
  
|オペランド|関係演算子|等価演算子|  
|-------------|-------------------------|-----------------------|  
|両方のオペランドがノード セットの場合|1 つのセットにノードがあり、2 番目のセットにノードがあり、**文字列**値の比較が TRUE である場合にのみ TRUE。|同じ。|  
|1 つはノード セット、もう 1 つは**文字列**です。|**数値**に変換される場合、ノード セット内にノードがある場合にのみ TRUE を**返**す場合は、数値に変換された**文字列**との比較が TRUE です。|TRUE を指定すると、ノード セット内にノードが存在し、**文字列**に変換されるときに、その**ノードと文字列**の比較は TRUE になります。|  
|1 つはノード セット、もう 1 つは**数値**です。|**数値**に変換される場合にノード セットにノードがある場合にのみ TRUE を**返**します。|同じ。|  
|1 つはノード セット、もう 1 つは**ブール値**です。|TRUE を指定すると、ノード セットにノードがあり、**ブール値**に変換されてから**数値**に変換された場合にのみ、そのノードと数値**に変換**された**ブール値**の比較は TRUE になります。|TRUE を指定すると、ノード セット内にノードが存在し、**ブール値**に変換される場合にのみ **、ブール値**との比較は TRUE になります。|  
|どちらもノード セットでない場合|両方のオペランドを**数値**に変換してから比較します。|両方のオペランドを共通のデータ型に変換し比較。 どちらかが**ブール型**の場合は**ブール型**に変換し、どちらかが**数値**の場合は**数値を返**します。それ以外の場合は、**文字列**に変換します。|  
  
> [!NOTE]  
>  XPath 関係演算子は常にオペランドを**数値**に変換するため、**文字列**比較はできません。 日付比較を含めるために、SQL Server 2000 では、XPath 仕様に対してこのバリエーションが提供されます: リレーショナル演算子が**文字列**と**文字列**を比較する場合、ノードセットを**文字列**に設定するか、文字列値のノード セットを文字列値のノード セットに設定すると、**文字列**比較 (**数値**比較ではない) が実行されます。  
  
## <a name="node-set-conversions"></a>ノード セット変換  
 ノード セット変換は常に直感的なものとは限りません。 ノード セットは、セットの最初のノードのみの文字列値を取得することによって**文字列**に変換されます。 ノード セットは **、文字列**に変換し、**文字列**を数値**に変換**することによって **、数値**に変換されます。 ノード セットは、その存在をテストすることによって**boolean**に変換されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ノード セットで位置の選択は実行されません。たとえば、XPath クエリ `Customer[3]` は 3 番目の顧客を意味しますが、このような位置の選択は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではサポートされていません。 したがって、XPath 仕様で説明されているノード セットから**文字列**への変換、またはノード セットから**番号**への変換は実装されません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、XPath 仕様で "先頭" の意味で指定されているものが "任意" の意味として扱われます。 たとえば、W3C XPath 仕様に基づいて、XPath`Order[OrderDetail/@UnitPrice > 10.0]`クエリは **、10.0**より大きい単価を持つ最初の**注文詳細**を持つ注文を選択します。 では[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この XPath クエリは **、10.0**より大きい単価を持つ**注文明細**を持つ注文を選択します。  
  
 **ブール値**への変換は存在テストを生成します。したがって、XPath クエリ`Products[@Discontinued=true()]`は、SQL 式 "Products.生産 = 1" ではなく、SQL 式 "Products.で中止された NULL ではありません" と同等です。 クエリを後者の SQL 式と同等にするには、まずノード セットを**数値**などの**ブール型**以外の型に変換します。 たとえば、「 `Products[number(@Discontinued) = true()]` 」のように入力します。  
  
 大半の演算子は、ノード セット内の 1 つ以上のノードに対して TRUE であれば TRUE となるように定義されているので、これらの演算はノード セットが空の場合は常に FALSE となります。 したがって、A が空の場合、`A = B` と `A != B` は両方とも FALSE になり、`not(A=B)` と `not(A!=B)` は TRUE になります。  
  
 通常、データベース内の列の値が**null**でない場合、列にマップされる属性または要素が存在します。 行にマップされる要素は、子が存在する場合に存在します。  
  
> [!NOTE]  
>  定数でアノーティの要素**は**常に存在します。 したがって、XPath 述語は **、定数**要素では使用できません。  
  
 ノード セットが**文字列**または**数値**に変換されると、その XDR 型 (存在する場合) が、アノ付きスキーマで検査され、その型を使用して必要な変換が決定されます。  
  
## <a name="mapping-xdr-data-types-to-xpath-data-types"></a>XDR データ型から XPath データ型へのマッピング  
 ノードの XPath データ型は、次の表に示すように、スキーマの XDR データ型から派生します (ノード**EmployeeID**は説明用に使用されます)。  
  
|XDR データ型|同等の<br /><br /> XPath データ型|使用される SQL Server 変換|  
|-------------------|------------------------------------|--------------------------------|  
|Nonebin.base64bin.hex|該当なし|NoneEmployeeID|  
|boolean|boolean|CONVERT(bit, EmployeeID)|  
|number、int、float,i1、i2、i4、i8、r4、r8ui1、ui2、ui4、ui8|number|CONVERT(float(53), EmployeeID)|  
|id、idref、idrefsentity、entities、enumerationnotation、nmtoken、nmtokens、chardate、Timedate、Time.tz、string、uri、uuid|string|CONVERT(nvarchar(4000), EmployeeID, 126)|  
|fixed14.4|N/A (XDR データ型 fixed14.4 に相当する XPath のデータ型はありません)|CONVERT(money, EmployeeID)|  
|date|string|LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)|  
|time<br /><br /> time.tz|string|SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)|  
  
 日付と時刻の変換は[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]**、datetime**データ型または**文字列**を使用して値がデータベースに格納されているかどうかに関係なく機能するように設計されています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime**データ型は **、タイムゾーン**を使用せず、XML**時刻**データ型よりも精度が小さいことに注意してください。 **タイムゾーン**データ型または追加の精度を含めるには、**文字列**型を[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用してデータを格納します。  
  
 ノードが XDR データ型から XPath データ型に変換される場合は、1 つの XPath データ型から別の XPath データ型へ、追加の変換が必要になることがあります。 たとえば、次の XPath クエリを考えてみます。  
  
```  
(@m + 3) = 4  
```  
  
 @m **fixed14.4** XDR データ型の場合、XDR データ型から XPath データ型への変換は、次のように実行されます。  
  
```  
CONVERT(money, m)  
```  
  
 この変換では、ノード`m`は**fixed14.4**から**money**に変換されます。 しかし、値 3 を加算するには追加の変換が必要になります。  
  
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
||X が不明|X は**文字列です**|X は**数字です**|X は**ブール値**|  
|string(X)|CONVERT (nvarchar(4000), X, 126)|-|CONVERT (nvarchar(4000), X, 126)|CASE WHEN X THEN N'true' ELSE N'false' END|  
|number(X)|CONVERT (float(53), X)|CONVERT (float(53), X)|-|CASE WHEN X THEN 1 ELSE 0 END|  
|boolean(X)|-|レン(X) > 0|X != 0|-|  
  
## <a name="examples"></a>例  
  
### <a name="a-convert-a-data-type-in-an-xpath-query"></a>A. XPath クエリ内のデータ型を変換する  
 注釈付き XSD スキーマに対して指定された次の XPath クエリでは、クエリは **、EmployeeID**属性値が E-1 の**Employee**ノードをすべて**選択します。**  
  
 `Employee[@EmployeeID="E-1"]`  
  
 クエリ内の述語は、次の SQL 式と等価です。  
  
 `N'E-' + CONVERT(nvarchar(4000), Employees.EmployeeID, 126) = N'E-1'`  
  
 **EmployeeID**は、XSD スキーマの id **(** idref 、**idrefs**、 **nmtoken**、 **nmtokens**など ) のデータ型値の 1 つであるため、前に説明した変換規則を使用して **、文字列****XPath**データ型に変換されます。 **idrefs**  
  
 `CONVERT(nvarchar(4000), Employees.EmployeeID, 126)`  
  
 文字列に "E-" プレフィックスが追加され、結果が `N'E-1'` と比較されます。  
  
### <a name="b-perform-several-data-type-conversions-in-an-xpath-query"></a>B. XPath クエリ内で複数のデータ型変換を実行する  
 注釈付き XSD スキーマに対して指定される XPath クエリ `OrderDetail[@UnitPrice * @OrderQty > 98]` を考えてみます。  
  
 この XPath クエリは、述語`@UnitPrice * @OrderQty > 98`を**\<** 満たすすべての OrderDetail>要素を返します。 **UnitPrice**に、アポイントト付きスキーマの**fixed14.4**データ型が付けられた場合、この述語は SQL 式と同じです。  
  
 `CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice)) * CONVERT(float(53), OrderDetail.OrderQty) > CONVERT(float(53), 98)`  
  
 XPath クエリ内の値を変換するとき、最初の変換では、XDR データ型を XPath データ型に変換します。 前の表で説明したように **、UnitPrice**の XSD データ型は**fixed14.4**であるため、最初に使用される変換は次のとおりです。  
  
```  
CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 算術演算子はオペランドを**XPath データ**型に変換するため、2 番目の変換 (XPath データ型から別の XPath データ型への変換) が適用され、値が**float(53)** **(float(53) が**XPath**数値**データ型に近い値に変換されます。  
  
```  
CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 **OrderQty**属性に XSD データ型がない場合 **、OrderQty**は 1 回の変換で**XPath**データ型に変換されます。  
  
```  
CONVERT(float(53), OrderDetail.OrderQty)  
```  
  
 同様に、値 98 は XPath データ型の**数値**に変換されます。  
  
```  
CONVERT(float(53), 98)  
```  
  
> [!NOTE]  
>  スキーマで使用されている XSD データ型がデータベースの基になる[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型と互換性がない場合、または XPath データ型変換が実行できない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、エラーが返されることがあります。 たとえば **、EmployeeID**属性に**id-prefix**アノテーションが付けられている場合 **、EmployeeID**には`Employee[@EmployeeID=1]`id**プレフィックス**の注釈があり、数値に変換できないため、XPath はエラーを生成**します**。  
  
  
