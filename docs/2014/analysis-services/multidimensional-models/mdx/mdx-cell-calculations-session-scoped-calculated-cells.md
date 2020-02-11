---
title: セッションスコープの計算されるセルを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- session-scoped calculated members [MDX]
ms.assetid: f2d14a89-6286-4e74-9afb-091076f93f21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4388ef278c0762184859162dc55f656aae1c9a15
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66074427"
---
# <a name="creating-session-scoped-calculated-cells"></a>セッション スコープの計算されるセルの作成
    
> [!IMPORTANT]  
>  この構文は非推奨とされます。 代わりに、MDX 割り当てを使用してください。 割り当ての詳細については、「[基本的な MDX スクリプト &#40;MDX&#41;](the-basic-mdx-script-mdx.md)」を参照してください。  
  
 同じセッション内のすべてのクエリで使用可能な計算されるセルを作成するには、 [CREATE CELL CALCULATION](/sql/mdx/mdx-data-definition-create-cell-calculation) ステートメントまたは [ALTER CUBE](/sql/mdx/mdx-data-definition-alter-cube) ステートメントを使用できます。 どちらのステートメントを使用しても結果は同じになります。  
  
## <a name="create-cell-calculation-syntax"></a>CREATE CELL CALCULATION の構文  
  
> [!IMPORTANT]  
>  この構文は非推奨とされます。 代わりに、MDX 割り当てを使用してください。 割り当ての詳細については、「[基本的な MDX スクリプト &#40;MDX&#41;](the-basic-mdx-script-mdx.md)」を参照してください。  
  
 セッション スコープの計算されるセルを定義するために CREATE CELL CALCULATION ステートメントを使用するには、次の構文を使用します。  
  
```  
CREATE CELL CALCULATION Cube_Expression.<CREATE CELL CALCULATION body clause>  
  
<CREATE CELL CALCULATION body clause> ::=CellCalc_Identifier FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
## <a name="alter-cube-syntax"></a>ALTER CUBE の構文  
  
> [!IMPORTANT]  
>  この構文は非推奨とされます。 代わりに、MDX 割り当てを使用してください。 割り当ての詳細については、「[基本的な MDX スクリプト &#40;MDX&#41;](the-basic-mdx-script-mdx.md)」を参照してください。  
  
 セッション スコープの計算されるセルを定義するために ALTER CUBE ステートメントを使用するには、次の構文を使用します。  
  
```  
ALTER CUBE Cube_Identifier CREATE CELL CALCULATION  
FOR String_Expression AS 'MDX_Expression'   
   [ <CREATE CELL CALCULATION property clause> [ , <CREATE CELL CALCULATION property clause> ... ] ]  
  
<CREATE CELL CALCULATION property clause> ::=  
   ( CONDITION = 'Logical_Expression' ) |   
   ( DISABLED = { TRUE | FALSE } ) |   
   ( DESCRIPTION =String_Expression ) |   
   ( CALCULATION_PASS_NUMBER = Integer_Expression ) |   
   ( CALCULATION_PASS_DEPTH = Integer_Expression ) |   
   ( SOLVE_ORDER = Integer_Expression ) |   
   ( FORMAT_STRING = String_Expression ) |   
   ( CellProperty_Identifier = Scalar_Expression )  
```  
  
 
  `String_Expression` 値には、直交する 1 次元の MDX セット式のリストを指定します。それぞれの式は、次の表のいずれかのセット カテゴリに解決される必要があります。  
  
|カテゴリ|[説明]|  
|--------------|-----------------|  
|空セット|空セットに解決される MDX セット式。 この場合、計算されるセルのスコープはキューブ全体です。|  
|単一メンバー セット|1 つのメンバーに解決される MDX セット式。|  
|レベル メンバーのセット|単一レベルのメンバーに解決される MDX セット式。 この例としては、 *Level_Expression*があります。`Members` MDX 関数です。 計算されるメンバーを含めるには、 *Level_Expression*を使用します。`AllMembers` MDX 関数です。<br /><br /> 詳細については、「[AllMembers (MDX)](/sql/mdx/allmembers-mdx)」を参照してください。|  
|子孫のセット|指定したメンバーの子孫に解決される MDX セット式。 この例`Descendants`として、(*Member_Expression*、 *Level_Expression*、 *Desc_Flag*) MDX 関数があります。<br /><br /> 詳細については、「[Descendants (MDX)](/sql/mdx/descendants-mdx)」を参照してください。|  
  
## <a name="see-also"></a>参照  
 [Mdx &#40;MDX でのセル計算の作成&#41;](../../multidimensional-models-olap-logical-cube-objects/calculations.md)  
  
  
