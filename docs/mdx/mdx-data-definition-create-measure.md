---
title: CREATE MEASURE ステートメント (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3bac5d7d067186e2b84277a5c0dc02cd31cba011
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86967383"
---
# <a name="mdx-data-definition---create-measure"></a>MDX データ操作 - CREATE MEASURE


  テーブルモデルにメジャーを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE MEASURE Table_Name[Measure_Name] = DAX_Expression  
[; CREATE MEASURE ...n]  
  
```  
  
## <a name="arguments"></a>引数  
 *Table_Name*  
 メジャーが作成されるテーブルの名前を指定する有効な文字列リテラルです。  
  
 *Measure_Name*  
 メジャー名を提供する有効な文字列リテラルです。  
  
 *DAX_Expression*  
 1つのスカラー値を返す有効な DAX 式です。  
  
## <a name="remarks"></a>注釈  
 *Measure_Name*は、角かっこで囲む必要があります。  
  
 CREATE MEASURE ステートメントは、MDX スクリプト定義内でのみ使用できます。「 [MdxScript 要素 &#40;ASSL&#41;](https://docs.microsoft.com/analysis-services/assl/objects/mdxscript-element-assl?view=asallproducts-allversions)」を参照してください。  
  
 また、1つのクエリで使用するために、計算されるメンバーを定義することもできます。 1 つのクエリに限定される計算されるメンバーを定義するには、SELECT ステートメントで WITH 句を使用します。 詳細については、「 [MDX でのメジャーの作成](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-building-measures)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Mdx&#41;&#40;mdx データ定義ステートメント](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
