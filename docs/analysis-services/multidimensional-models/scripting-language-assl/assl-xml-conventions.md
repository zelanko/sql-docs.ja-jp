---
title: "ASSL XML 規則 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- whitespace [Analysis Services Scripting Language]
- trailing whitespace
- XSD data types [Analysis Services Scripting Language]
- inheritance [Analysis Services Scripting Language]
- cardinality [Analysis Services Scripting Language]
- white space [Analysis Services Scripting Language]
- ASSL, XML conventions
- defaults [Analysis Services Scripting Language]
- leading whitespace
- Analysis Services Scripting Language, XML conventions
- XML [Analysis Services Scripting Language]
- hierarchies [Analysis Services Scripting Language]
- inherited defaults [Analysis Services Scripting Language]
ms.assetid: bce4edad-4420-41ce-9672-8c00c5c0dec6
caps.latest.revision: "24"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 9627648fa47b750f4b9b98b45b5878cea0806961
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="assl-xml-conventions"></a>ASSL XML 規則
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Analysis Services スクリプト言語 (ASSL) は、定義されている子要素を含めることができる要素型のセットとしてオブジェクトの階層を表します。  
  
 ASSL では、次の XML 規則を使用してオブジェクトの階層を表します。  
  
-   'xml:lang' などの標準の XML 属性を除き、すべてのオブジェクトとプロパティを要素として表します。  
  
-   要素名および列挙値の両方 pascal 形式の Microsoft .NET Framework の名前付け規則に従っていないアンダー スコアで大文字小文字の区別します。  
  
-   すべての値の大文字と小文字の区別が保持されます。 列挙の値も大文字と小文字が区別されます。  
  
 これらの規則の他にも、Analysis Services は基数、継承、空白文字、データ型、既定値などに関する一定の規則に従います。  
  
## <a name="cardinality"></a>Cardinality  
 要素に 1 より大きい基数がある場合は、この要素をカプセル化する XML 要素のコレクションがあります。 コレクションの名前は、コレクションに含まれている要素の複数形を使用します。 たとえば、次の XML フラグメントを表す、**ディメンション**内のコレクション、**データベース**要素。  
  
 `<Database>`  
  
 `…`  
  
 `<Dimensions>`  
  
 `<Dimension>`  
  
 `...`  
  
 `</Dimension>`  
  
 `<Dimension>`  
  
 `...`  
  
 `</Dimension>`  
  
 `</Dimensions>`  
  
 `</Database>`  
  
 ``  
  
 要素の順序は重要ではありません。  
  
## <a name="inheritance"></a>継承  
 継承は、重複しているが大幅に異なるプロパティのセットを持つ、明確に区別されるオブジェクトがある場合に使用されます。 このように重複しているが明確に区別されるオブジェクトの例として、仮想キューブ、リンク キューブ、および標準キューブがあります。 個別のオブジェクトが重複している、Analysis Services は、標準**型**からの継承を示すために XML インスタンスの Namespace 属性です。 たとえば、次の XML が番組をフラグメント方法、**型**属性を識別するかどうか、**キューブ**要素が標準キューブまたは仮想キューブからの継承します。  
  
 `<Cubes>`  
  
 `<Cube xsi:type=”RegularCube”>`  
  
 `<Name>Sales</Name>`  
  
 `...`  
  
 `</Cube>`  
  
 `<Cube xsi:type=”VirtualCube”>`  
  
 `<Name>SalesAndInventory</Name>`  
  
 `...`  
  
 `</Cube>`  
  
 `</Cubes>`  
  
 ``  
  
 継承は通常、複数の型に同じ名前のプロパティがある場合は使用されません。 たとえば、**名前**と**ID**多くの要素にプロパティが表示されますが、これらのプロパティが抽象型に昇格されていません。  
  
## <a name="whitespace"></a>空白文字  
 要素値内の空白文字が保持されます。 ただし、先頭と末尾の空白文字は常に切り捨てられます。 たとえば、次の要素には同じテキストがありますが、そのテキスト内の空白文字の数が異なるので、別の値として扱われます。  
  
 `<Description>My text<Description>`  
  
 `<Description>My  text<Description>`  
  
 ``  
  
 しかし、次の要素は先頭と末尾の空白文字のみが異なるので、同じ値として扱われます。  
  
 `<Description>My text<Description>`  
  
 `<Description>  My text  <Description>`  
  
 ``  
  
## <a name="data-types"></a>データ型  
 Analysis Services では、次のように XML スキーマ定義言語 (XSD) の標準的なデータ型を使用します。  
  
 **Int**  
 -231 ～ 231 - 1 の範囲の整数値。  
  
 **Long**  
 -263 ～ 263 - 1 の範囲の整数値。  
  
 **文字列**  
 次のグローバル ルールに従う文字列値。  
  
-   制御文字は除去されます。  
  
-   先頭と末尾の空白文字は切り捨てられます。  
  
-   内部の空白文字は保持されます。  
  
 **名前**と**ID**プロパティ文字列の要素の有効な文字に特別な制限もあります。 詳細については**名前**と**ID**規則を参照してください[ASSL オブジェクトとオブジェクトの特性](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-objects-and-object-characteristics.md)です。  
  
 **DateTime**  
 A **DateTime** .NET Framework の構造体。 A **DateTime**値が NULL にすることはできません。 サポートされる最小の日付、 **DataTime**データ型は 1601 年 1 月 1 日としてプログラマに利用できる**DateTime.MinValue**です。 サポートされる最小の日付には、ことを示します、 **DateTime**値がありません。  
  
 **ブール値**  
 {true, false} や {0, 1} のように値が 2 つだけの列挙。  
  
## <a name="default-values"></a>既定値  
 Analysis Services で使用される既定値を次の表に示します。  
  
|XML データ型|既定値|  
|-------------------|-------------------|  
|**ブール値**|False|  
|**文字列**|"" (空の文字列)|  
|**整数**または**長**|0 (ゼロ)|  
|**タイムスタンプ**|12時 00分: 00、1/1/0001 (に対応する、.NET フレームワーク**System.DateTime** 0 タイマー刻みで)|  
  
 要素が存在するが空の場合は、既定値ではなく NULL 文字列の値を含んでいるとして解釈されます。  
  
### <a name="inherited-defaults"></a>継承された既定値  
 オブジェクトに指定されているプロパティには、子または子孫オブジェクトの同じプロパティに既定値を提供するものがあります。 たとえば、 **Cube.StorageMode**の既定値は、 **Partition.StorageMode**です。 Analysis Services で継承された既定値に適用されるルールは、次のとおりです。  
  
-   子オブジェクトのプロパティが XML で NULL の場合、その値の既定値は継承された値になります。 ただし、サーバーから値をクエリする場合は、XML 要素の NULL 値が返されます。  
  
-   子オブジェクトのプロパティが子オブジェクトで直接設定されたか、または継承されたかをプログラムで判断することはできません。  
  
 一部の要素には、要素が欠落しているときに適用される既定値が定義されています。 たとえば、**ディメンション**次の XML フラグメント内の要素が同じもの**ディメンション**要素が含まれています、 **Visible**要素が他の**ディメンション**要素はありません。  
  
 `<Dimension>`  
  
 `<Name>Product</Name>`  
  
 `</Dimension>`  
  
 `<Dimension>`  
  
 `<Name>Product</ Name>`  
  
 `<Visible>true</Visible>`  
  
 `</Dimension>`  
  
 継承された既定値の詳細については、次を参照してください。 [ASSL オブジェクトとオブジェクトの特性](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-objects-and-object-characteristics.md)です。  
  
  
