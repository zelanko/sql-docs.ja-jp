---
title: CREATE CELL CALCULATION ステートメント (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7e69aa9e3da29abe054aaf272c5fe3ed12172a4d
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741301"
---
# <a name="mdx-data-definition---create-cell-calculation"></a>MDX データ定義のセル計算の作成


  キューブ内で指定されている組のセットに対して多次元式 (MDX) 式を評価する計算を作成します。  
  
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
 セル計算の名前を指定する有効な文字列です。  
  
 *Set_Expression*  
 セットを返す有効な MDX 式です。  
  
 *文字列*  
 有効な文字列値です。  
  
 *MDX_Expression*  
 有効な MDX 式です。  
  
 *Logical_Expression*  
 有効な MDX 論理式です。  
  
 *Integer*  
 有効な整数値です。  
  
 *Calculation_Name*  
 セル計算プロパティの名前を指定する有効な文字列です。  
  
 *Scalar_Expression*  
 有効な MDX スカラー式です。  
  
## <a name="remarks"></a>コメント  
 クライアント アプリケーションでは、計算されるセルを使用して、カスタム ロールアップ式や計算されるメンバーなどの場合のように、セルの全セットではなく特定セットのロールアップ値を指定できます。 たとえば、`{[Canada],[Time].[2000]}` によって定義されるセット内のセルに、特定の式によって定義される値を入れる、といった指定が可能です。 そのセットに含まれない他のセルは、通常の方法で処理されます。  
  
> [!NOTE]  
>  バッカスナウア記法 (BNF) の`{*(<comment> | <whitespace> | <newline>)}`として解析されます`{*}`の旧バージョンとの互換性。  
  
## <a name="see-also"></a>参照  
 [セッション スコープの計算されるセルの作成](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-session-scoped-calculated-cells.md)   
 [クエリ スコープのセル計算を作成する&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-query-scoped-cell-calculations.md)   
 [MDX でのセル計算の構築&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-build-cell-calculations.md)   
 [セル プロパティを使用して&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md)   
 [FORMAT_STRING の内容&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md)   
 [FORE_COLOR および BACK_COLOR の内容&#40;MDX&#41;](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md)   
 [MDX データ定義ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
