---
title: セル プロパティ (MDX) の使用 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 481d89abac98dee1095e55a9890cea100f6c4db6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="mdx-cell-properties---using-cell-properties"></a>MDX のセル プロパティのセル プロパティの使用
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  多次元式 (MDX) でのセル プロパティには、キューブなどの多次元データ  ソース内のセルの内容や書式に関する情報が含まれます。  
  
 MDX では、固有のセル プロパティを取得するために MDX SELECT ステートメント内で CELL PROPERTIES キーワードを使用できます。 固有セル プロパティは、主にセル データを視覚的に表示するために利用されます。  
  
## <a name="cell-properties-keyword-syntax"></a>CELL PROPERTIES キーワードの構文  
 MDX **SELECT** ステートメントの **CELL PROPERTIES** キーワードには、次の構文を使用します。  
  
```  
SELECT [<axis_specification>  
       [, <axis_specification>...]]  
  FROM [<cube_specification>]  
[WHERE [<slicer_specification>]]  
[<cell_props>]  
```  
  
 次の構文は、 `<cell_props>` 値の形式、およびこの値の中で **CELL PROPERTIES** キーワードと 1 つまたは複数の固有セル プロパティを使用する方法を示しています。  
  
```  
<cell_props> ::= CELL PROPERTIES <property> [, <property>...]  
```  
  
## <a name="supported-intrinsic-cell-properties"></a>サポートされる固有セル プロパティ  
 次の表は、 `<property>` 値の中で使用可能な固有セル プロパティを示しています。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|**ACTION_TYPE**|セルに対するアクションの種類を示すビットマスク。 このプロパティの値は、次のいずれか 1 つです。<br /><br /> **MDACTION_TYPE_URL**<br /><br /> **MDACTION_TYPE_HTML**<br /><br /> **MDACTION_TYPE_STATEMENT**<br /><br /> **MDACTION_TYPE_DATASET**<br /><br /> **MDACTION_TYPE_ROWSET**<br /><br /> **MDACTION_TYPE_COMMANDLINE**<br /><br /> **MDACTION_TYPE_PROPRIETARY**<br /><br /> **MDACTION_TYPE_REPORT**<br /><br /> **MDACTION_TYPE_DRILLTHROUGH**<br /><br /> <br /><br /> 注: WHERE 句内にセットを含むクエリの場合、ドリルスルー アクションは含まれません。|  
|**BACK_COLOR**|**VALUE** または **FORMATTED_VALUE** プロパティを表示するときの背景色。 詳しくは、「[FORE_COLOR および BACK_COLOR の内容 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md)」をご覧ください。|  
|**CELL_ORDINAL**|データセット内のセルの序数。|  
|**FONT_FLAGS**|フォントの詳細な文字飾りを示すビットマスク。 この値は、次の 1 つ以上の定数に対するビットごとの OR 演算の結果です。<br /><br /> **MDFF_BOLD** = 1<br /><br /> **MDFF_ITALIC** = 2<br /><br /> **MDFF_UNDERLINE** = 4<br /><br /> **MDFF_STRIKEOUT** = 8<br /><br /> <br /><br /> たとえば、値 5 は、太字の (**MDFF_BOLD**) フォントと下線付きの (**MDFF_UNDERLINE**) フォントの文字飾りの組み合わせを表します。|  
|**FONT_NAME**|**VALUE** プロパティまたは **FORMATTED_VALUE** プロパティの表示に使用されるフォント。|  
|**FONT_SIZE**|**VALUE** プロパティまたは **FORMATTED_VALUE** プロパティの表示に使用されるフォント サイズ。|  
|**FORE_COLOR**|**VALUE** または **FORMATTED_VALUE** プロパティを表示するときの前景色。 詳しくは、「[FORE_COLOR および BACK_COLOR の内容 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md)」をご覧ください。|  
|**FORMAT**|**FORMAT_STRING**と同じです。|  
|**FORMAT_STRING**|**FORMATTED_VALUE** プロパティ値の作成に使用する書式文字列。 詳しくは、「[FORMAT_STRING の内容 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md)」をご覧ください。|  
|**FORMATTED_VALUE**|**VALUE** プロパティの表示の書式設定を表す文字列。|  
|**LANGUAGE**|**FORMAT_STRING** を適用するロケール。 **LANGUAGE** は通常、通貨変換のために使用されます。|  
|**UPDATEABLE**|セルが更新可能かどうかを示す値。 このプロパティの値は、次のいずれか 1 つです。|  
||**MD_MASK_ENABLED** (0x00000000)   セルは更新可能です。|  
||**MD_MASK_NOT_ENABLED** (0x10000000)   セルは更新できません。|  
||**CELL_UPDATE_ENABLED** (0x00000001)   セルはセルセット内で更新可能です。|  
||**CELL_UPDATE_ENABLED_WITH_UPDATE** (0x00000002)   セルは UPDATE ステートメントによって更新可能です。 書き込み可能でないリーフ セルが更新される場合、UPDATE は失敗する可能性があります。|  
||**CELL_UPDATE_NOT_ENABLED_FORMULA** (0x10000001)   セルの座標の中に計算されるメンバーが含まれているため、セルを更新できません。WHERE 句内のセットと共にセルが取得されました。 数式がセルの値に影響を与える、あるいは計算されるセルが集計パス上にあるとしても、セルの更新は行われます。 この場合、結果が計算に影響されるため、セルの最終的な値は更新後の値にならない可能性があります。|  
||**CELL_UPDATE_NOT_ENABLED_NONSUM_MEASURE** (0x10000002)   合計でないメジャー (カウント数、最小値、最大値、個別カウント、および準加法) は更新できないため、セルは更新できません。|  
||**CELL_UPDATE_NOT_ENABLED_NACELL_VIRTUALCUBE** (0x10000003)   セルが存在しない (メジャーと、そのメジャーが属するメジャー グループとは無関係なディメンション メンバーの交差部分にセルがある) ため、セルは更新できません。|  
||**CELL_UPDATE_NOT_ENABLED_SECURE** (0x10000005)    セルが保護されているため、セルは更新できません。|  
||**CELL_UPDATE_NOT_ENABLED_CALCLEVEL** (0x10000006)   将来の使用のために予約されています。|  
||**CELL_UPDATE_NOT_ENABLED_CANNOTUPDATE** (0x10000007)   内部的な理由のため、セルは更新できません。|  
||**CELL_UPDATE_NOT_ENABLED_INVALIDDIMENSIONTYPE** (0x10000009)   マイニング モデル ディメンション、間接ディメンション、データ マイニング ディメンションでは更新がサポートされないため、セルは更新できません。|  
|**VALUE**|書式設定されていないセルの値。|  
  
 必須のセル プロパティは、 **CELL_ORDINAL**、 **FORMATTED_VALUE**、および **VALUE** のみです。 固有またはプロバイダー固有を問わず、すべてのセル プロパティは、そのデータ型およびプロバイダーのサポートを含めて、 **PROPERTIES** スキーマ行セットで定義します。 **PROPERTIES** スキーマ行セットの詳細については、「 [MDSCHEMA_PROPERTIES 行セット](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-properties-rowset.md)」を参照してください。  
  
 既定では、 **CELL PROPERTIES** キーワードが使用されない場合、返されるセル プロパティは **VALUE**、 **FORMATTED_VALUE**、および **CELL_ORDINAL** です (順序もこのとおり)。 **CELL PROPERTIES** キーワードが使用されている場合は、キーワードで明示的に記述されたセル プロパティだけが返されます。  
  
 次の例は、MDX クエリでの **CELL PROPERTIES** キーワードの使用法を示しています。  
  
```  
SELECT  
   {[Measures].[Reseller Gross Profit]} ON COLUMNS,  
   {[Reseller].[Reseller Type].[Reseller Name].Members} ON ROWS  
FROM [Adventure Works]  
CELL PROPERTIES VALUE, FORMATTED_VALUE, FORMAT_STRING, FORE_COLOR, BACK_COLOR  
```  
  
 平面的な行セットを返す MDX クエリの場合、セル プロパティは返されません。この場合、各セルは **FORMATTED_VALUE** セル プロパティだけが返されたかのように表示されます。  
  
## <a name="setting-cell-properties"></a>セル プロパティの設定  
 セル プロパティは、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のさまざまな場所で設定できます。 たとえば、Format String プロパティは、 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]のキューブ エディターの [キューブ構造] タブで、標準メジャーに対して設定できます。同じプロパティをキューブ エディターの [計算] タブで、キューブで定義されている計算されるメジャーに対して設定できます。クエリの WITH 句で定義されている計算されるメジャーも、その書式設定文字列をそこで定義されます。次のクエリでは、計算されるメジャーに対してセル プロパティを設定する方法を示しています。  
  
```  
WITH MEMBER MEASURES.CELLPROPERTYDEMO AS [Measures].[Internet Sales Amount]  
, FORE_COLOR=RGB(0,0,255)  
, BACK_COLOR=IIF([Measures].[Internet Sales Amount]>7000000, RGB(255,0,0), RGB(0,255,0))  
, FONT_SIZE=10  
, FORMAT_STRING='#,#.000'  
SELECT MEASURES.CELLPROPERTYDEMO ON 0,  
[Date].[Calendar Year].[Calendar Year].MEMBERS ON 1  
FROM [Adventure Works]  
CELL PROPERTIES VALUE, FORMATTED_VALUE, FORE_COLOR, BACK_COLOR, FONT_SIZE  
```  
  
## <a name="see-also"></a>参照  
 [MDX クエリの基礎と #40 です。Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
