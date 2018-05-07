---
title: CalculationPassValue (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CALCULATIONPASSVALUE
dev_langs:
- kbMDX
helpviewer_keywords:
- CalculationPassValue function
ms.assetid: 1b4012cb-c8c7-441a-bb9c-59430703b189
caps.latest.revision: 45
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: f15c5cec26e55a403bea58883cf5de978b6a2b45
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="calculationpassvalue-mdx"></a>CalculationPassValue (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  キューブに対して指定された計算パスを評価し、多次元式 (MDX) 式の数値または文字列値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
      Numeric syntax  
CalculationPassValue(Numeric_Expression,Pass_Value [, ABSOLUTE | RELATIVE [,ALL]])  
String syntax  
CalculationPassValue(String_Expression ,Pass_Value [, ABSOLUTE | RELATIVE [,ALL]])  
```  
  
## <a name="arguments"></a>引数  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
 *String_Expression*  
 有効な文字列式です。通常は、文字列として表された数値を返すセル座標の有効な多次元式 (MDX) 式です。  
  
 *Pass_Value*  
 計算パス番号を指定する有効な数値式です。  
  
 ABSOLUTE  
 指定するアクセス フラグ値、 *Pass_Value*パラメーターには、計算パスの 0 から始まるインデックスが含まれています。 アクセス フラグ値が指定されていない場合は、ABSOLUTE が既定のアクセス フラグ値になります。  
  
 RELATIVE  
 指定するアクセス フラグ値、 *Pass_Value*パラメーターには、トリガーを起動する計算の計算パスからの相対的なオフセットが含まれています。 このオフセットが 0 より小さい計算パス インデックスになる場合は、計算パス 0 が使用されます。したがって、エラーは発生しません。  
  
 ALL  
 このフラグが設定されると、ストレージ エンジンによって読み込まれる値以外はすべて NULL になります。 このフラグが設定されていない場合は、何の計算も適用されずに値が集計されます。  
  
## <a name="remarks"></a>解説  
 数値式が指定されると、この関数は、指定された計算パス内で指定されている (さらに、必要に応じてアクセス フラグとアクセス フラグ修飾子で修飾されている) MDX 数値式を評価し、数値を返します。  
  
 文字列式を指定する場合を返し、文字列値、指定された計算パスで指定された MDX 文字列式を評価することによって調整必要に応じてアクセス フラグとアクセス フラグ修飾子で*です。*  
  
 再帰を自動での解決方法[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、この関数は、小さな実際に使用します。  
  
> [!NOTE]  
>  管理者のみが使用できる、 **CalculationPassValue** MDX スクリプト内の関数。 管理者権限を持たないロールのコンテキストでこの関数を含んだ MDX スクリプトを実行すると、エラーが発生します。  
  
## <a name="see-also"></a>参照  
 [CalculationCurrentPass & #40 です。MDX と #41 です。](../mdx/calculationcurrentpass-mdx.md)   
 [IIf &#40;MDX&#41;](../mdx/iif-mdx.md)   
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
