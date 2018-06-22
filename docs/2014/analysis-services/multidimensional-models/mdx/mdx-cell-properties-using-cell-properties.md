---
title: セル プロパティ (MDX) の使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- intrinsic cell properties [MDX]
- cells [MDX]
- cell properties [MDX]
- CELL PROPERTIES keyword
ms.assetid: a593c74d-8c5e-485e-bd92-08f9d22451d4
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 496fbb18fa454b17b78dc54d598a96a88e5dcb8f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071768"
---
# <a name="using-cell-properties-mdx"></a>セル プロパティの使用 (MDX)
  多次元式 (MDX) でのセル プロパティには、キューブなどの多次元データ  ソース内のセルの内容や書式に関する情報が含まれます。  
  
 MDX では、固有のセル プロパティを取得するために MDX SELECT ステートメント内で CELL PROPERTIES キーワードを使用できます。 固有セル プロパティは、主にセル データを視覚的に表示するために利用されます。  
  
## <a name="cell-properties-keyword-syntax"></a>CELL PROPERTIES キーワードの構文  
 次の構文を使用して、 `CELL PROPERTIES` MDX のキーワード`SELECT`ステートメント。  
  
```  
SELECT [<axis_specification>  
       [, <axis_specification>...]]  
  FROM [<cube_specification>]  
[WHERE [<slicer_specification>]]  
[<cell_props>]  
```  
  
 次の構文は、`<cell_props>` 値の形式、およびこの値の中で `CELL PROPERTIES` キーワードと 1 つまたは複数の固有セル プロパティを使用する方法を示しています。  
  
```  
<cell_props> ::= CELL PROPERTIES <property> [, <property>...]  
```  
  
## <a name="supported-intrinsic-cell-properties"></a>サポートされる固有セル プロパティ  
 次の表は、 `<property>` 値の中で使用可能な固有セル プロパティを示しています。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|`ACTION_TYPE`|セルに対するアクションの種類を示すビットマスク。 このプロパティの値は、次のいずれか 1 つです。<br /><br /> **MDACTION_TYPE_URL**<br /><br /> **MDACTION_TYPE_HTML**<br /><br /> **MDACTION_TYPE_STATEMENT**<br /><br /> **MDACTION_TYPE_DATASET**<br /><br /> **MDACTION_TYPE_ROWSET**<br /><br /> **MDACTION_TYPE_COMMANDLINE**<br /><br /> **MDACTION_TYPE_PROPRIETARY**<br /><br /> **MDACTION_TYPE_REPORT**<br /><br /> **MDACTION_TYPE_DRILLTHROUGH**<br /><br /> <br /><br /> 注: WHERE 句内にセットを含むクエリの場合、ドリルスルー アクションは含まれません。|  
|**BACK_COLOR**|`VALUE` または `FORMATTED_VALUE` プロパティを表示するときの背景色。 詳しくは、「[FORE_COLOR および BACK_COLOR の内容 &#40;MDX&#41;](mdx-cell-properties-fore-color-and-back-color-contents.md)」をご覧ください。|  
|`CELL_ORDINAL`|データセット内のセルの序数。|  
|**FONT_FLAGS**|フォントの詳細な文字飾りを示すビットマスク。 たとえば、値 5 が太字の組み合わせを表します (`MDFF_BOLD`) と下線 (`MDFF_UNDERLINE`) フォントの文字飾り。 この値は、次の 1 つ以上の定数に対するビットごとの OR 演算の結果です。<br /><br /> `MDFF_BOLD` = 1<br /><br /> `MDFF_ITALIC` = 2<br /><br /> `MDFF_UNDERLINE` = 4<br /><br /> `MDFF_STRIKEOUT` = 8|  
|**FONT_NAME**|表示するために使用するフォント、`VALUE`または`FORMATTED_VALUE`プロパティです。|  
|**FONT_SIZE**|`VALUE` または `FORMATTED_VALUE` プロパティの表示に使用するフォント サイズ。|  
|**FORE_COLOR**|`VALUE` または `FORMATTED_VALUE` プロパティを表示するときの前景色。 詳しくは、「[FORE_COLOR および BACK_COLOR の内容 &#40;MDX&#41;](mdx-cell-properties-fore-color-and-back-color-contents.md)」をご覧ください。|  
|`FORMAT`|同じ`FORMAT_STRING`です。|  
|`FORMAT_STRING`|作成するために使用する書式指定文字列、`FORMATTED_VALUE`プロパティの値。 詳しくは、「[FORMAT_STRING の内容 &#40;MDX&#41;](mdx-cell-properties-format-string-contents.md)」をご覧ください。|  
|`FORMATTED_VALUE`|文字列の表示の書式設定を表す、`VALUE`プロパティです。|  
|`LANGUAGE`|`FORMAT_STRING` を適用するロケール。 `LANGUAGE` 通常、通貨変換のため使用されます。|  
|`UPDATEABLE`|セルが更新可能かどうかを示す値。 このプロパティの値は、次のいずれか 1 つです。<br /><br /> `MD_MASK_ENABLED` (0x00000000) セルを更新することができます。<br /><br /> `MD_MASK_NOT_ENABLED` (0x10000000) セルを更新することはできません。<br /><br /> `CELL_UPDATE_ENABLED` (0x00000001) セルセットのセルを更新することができます。<br /><br /> `CELL_UPDATE_ENABLED_WITH_UPDATE` (0x00000002) update ステートメントで、セルを更新します。 書き込み可能でないリーフ セルが更新される場合、UPDATE は失敗する可能性があります。<br /><br /> `CELL_UPDATE_NOT_ENABLED_FORMULA` セルにすることはできません (0x10000001) セルの座標間での計算されるメンバーがあるために、更新セルは、セットで、where 句で取得された句。 数式がセルの値に影響を与える、あるいは計算されるセルが集計パス上にあるとしても、セルの更新は行われます。 この場合、結果が計算に影響されるため、セルの最終的な値は更新後の値にならない可能性があります。<br /><br /> `CELL_UPDATE_NOT_ENABLED_NONSUM_MEASURE` (0x10000002)、合計でないメジャー (count、min、max、個別カウント、準加法) を更新されないため、セルは更新できません。<br /><br /> `CELL_UPDATE_NOT_ENABLED_NACELL_VIRTUALCUBE` (0x10000003) で、メジャーの交差部分にあるメジャーのメジャー グループに関連付けられていないディメンション メンバー、セルが存在しないため、セルは更新できません。<br /><br /> `CELL_UPDATE_NOT_ENABLED_SECURE` (0x10000005) セルのセキュリティで保護されているため、セルは更新できません。<br /><br /> `CELL_UPDATE_NOT_ENABLED_CALCLEVEL` (0x10000006) 将来使用するために予約されています。<br /><br /> `CELL_UPDATE_NOT_ENABLED_CANNOTUPDATE` (0x10000007) 内部の理由によって、セルは更新できません。<br /><br /> `CELL_UPDATE_NOT_ENABLED_INVALIDDIMENSIONTYPE` (0x10000009) マイニング モデルでは、間接損害、またはデータ マイニング ディメンションでは、更新はサポートされていないため、セルは更新できません。|  
|`VALUE`|書式設定されていないセルの値。|  
  
 のみ、 `CELL_ORDINAL`、 `FORMATTED_VALUE`、および`VALUE`セル プロパティが必要です。 固有またはプロバイダー固有を問わず、すべてのセル プロパティは、そのデータ型およびプロバイダーのサポートを含めて、`PROPERTIES` スキーマ行セットで定義します。 詳細については、`PROPERTIES`スキーマ行セットを参照してください[MDSCHEMA_PROPERTIES 行セット](../../schema-rowsets/ole-db-olap/mdschema-properties-rowset.md)です。  
  
 既定では場合、`CELL PROPERTIES`キーワードが使用しない場合、返されるセル プロパティは`VALUE`、 `FORMATTED_VALUE`、および`CELL_ORDINAL`(その順序で)。 場合、`CELL PROPERTIES`キーワードを使用すると、キーワードを使用して明示的に記されてセル プロパティだけが返されます。  
  
 次の例での使用、 `CELL PROPERTIES` MDX クエリでキーワード。  
  
```  
SELECT  
   {[Measures].[Reseller Gross Profit]} ON COLUMNS,  
   {[Reseller].[Reseller Type].[Reseller Name].Members} ON ROWS  
FROM [Adventure Works]  
CELL PROPERTIES VALUE, FORMATTED_VALUE, FORMAT_STRING, FORE_COLOR, BACK_COLOR  
```  
  
 フラットな行セットを返す MDX クエリのセル プロパティは返されませんこの場合、各セルはように、表現だけ、`FORMATTED_VALUE`セル プロパティが返されました。  
  
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
 [MDX クエリの基礎&#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  