---
title: CREATE CELL CALCULATION ステートメント (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CELL CALCULATION
- CREATE
- CALCULATION
- CELL
- CREATE_CELL_CALCULATION
- CREATE CELL
- CREATE CELL CALCULATION
dev_langs:
- kbMDX
helpviewer_keywords:
- calculations [Analysis Services], creating
- CREATE CELL CALCULATION statement
- cubes [Analysis Services], calculations
ms.assetid: 01ced1b3-ada1-4b55-b350-e4255c3cc679
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 07f8925db3b1a427129c37e589f37d8b028aae41
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-data-definition---create-cell-calculation"></a>MDX データ定義のセル計算の作成
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
## <a name="remarks"></a>解説  
 クライアント アプリケーションでは、計算されるセルを使用して、カスタム ロールアップ式や計算されるメンバーなどの場合のように、セルの全セットではなく特定セットのロールアップ値を指定できます。 たとえば、`{[Canada],[Time].[2000]}` によって定義されるセット内のセルに、特定の式によって定義される値を入れる、といった指定が可能です。 そのセットに含まれない他のセルは、通常の方法で処理されます。  
  
> [!NOTE]  
>  バッカスナウア記法 (BNF) の`{*(<comment> | <whitespace> | <newline>)}`として解析されます`{*}`の旧バージョンとの互換性。  
  
## <a name="see-also"></a>参照  
 [セッション スコープの計算されるセルの作成](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-session-scoped-calculated-cells.md)   
 [クエリ スコープのセル計算 &#40; を作成します。MDX と #41 です。](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-query-scoped-cell-calculations.md)   
 [MDX &#40; でのセル計算の作成MDX と #41 です。](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-build-cell-calculations.md)   
 [セルのプロパティ &#40; を使用します。MDX と #41 です。](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md)   
 [FORMAT_STRING の内容と #40 です。MDX と #41 です。](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md)   
 [FORE_COLOR および BACK_COLOR の内容と #40 です。MDX と #41 です。](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md)   
 [MDX データ定義ステートメント &#40;です。MDX と #41 です。](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
