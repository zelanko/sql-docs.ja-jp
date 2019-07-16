---
title: CREATE CELL CALCULATION ステートメント (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 411ae301c2f0ce858b7273c6bb721269f709b5c2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68098486"
---
# <a name="mdx-data-definition---create-cell-calculation"></a>MDX データ操作 - CREATE CELL CALCULATION


  キューブ内の組の指定されたセットに対して多次元式 (MDX) 式を評価する計算を作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
[WITH <CELL CALCULATION clause> Calculation_Name  
   [,WITH <CELL CALCULATION clause> Calculation_Name...n]  
CREATE CELL CALCULATION CURRENTCUBE | Cube_Name.Calculation_Name   
  
<CELL CALCULATION clause> ::=  
   FOR Set_Expression AS 'MDX_Expression'   
      [ [ CONDITION = 'Logical_Expression' ]   
    | [ DISABLED = { TRUE | FALSE } ]   
    | [ DESCRIPTION =String ]   
    | [ CALCULATION_PASS_NUMBER = Integer]   
    | [ CALCULATION_PASS_DEPTH = Integer]   
    | [ SOLVE_ORDER = Integer]   
    | [ Calculation_Name= Scalar_Expression ], ...n]  
```  
  
## <a name="arguments"></a>引数  
 *Cube_Name*  
 有効な文字列キューブ名を提供します。  
  
 *Calculation_Name*  
 セル計算の名前を提供する有効な文字列。  
  
 *Set_Expression*  
 セットを返す有効な MDX 式です。  
  
 *String*  
 有効な文字列値。  
  
 *MDX_Expression*  
 有効な MDX 式です。  
  
 *Logical_Expression*  
 有効な MDX 論理式です。  
  
 *Integer*  
 有効な整数値。  
  
 *Calculation_Name*  
 セル計算プロパティの名前を指定する有効な文字列。  
  
 *Scalar_Expression*  
 有効な MDX スカラー式です。  
  
## <a name="remarks"></a>コメント  
 計算されるセルを使用すると、クライアント アプリケーションの代わりに、特定のセルのセットのロールアップ値をことができますカスタム ロールアップ式または計算されるメンバーの場合と同様のセルのセット全体を指定します。 たとえば、`{[Canada],[Time].[2000]}` によって定義されるセット内のセルに、特定の式によって定義される値を入れる、といった指定が可能です。 通常、このセットに含まれていないその他の任意のセルが計算されます。  
  
> [!NOTE]  
>  バッカスナウア記法 (BNF) の`{*(<comment> | <whitespace> | <newline>)}`として解析されます`{*}`の下位互換性です。  
  
## <a name="see-also"></a>関連項目  
 [セッション スコープの計算されるセルを作成します。](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-session-scoped-calculated-cells.md)   
 [クエリ スコープのセル計算の作成 (MDX)](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-query-scoped-cell-calculations.md)   
 [MDX でのセル計算の構築&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-build-cell-calculations.md)   
 [セル プロパティの使用 &#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md)   
 [FORMAT_STRING の内容 (MDX)](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md)   
 [FORE_COLOR および BACK_COLOR の内容&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md)   
 [MDX データ定義ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
