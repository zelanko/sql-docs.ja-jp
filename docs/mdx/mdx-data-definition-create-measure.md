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
ms.openlocfilehash: 02c6d29bbebcc794e72f4ca960e3d9259de7205b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68892142"
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
  
## <a name="remarks"></a>Remarks  
 *Measure_Name*は、角かっこで囲む必要があります。  
  
 CREATE MEASURE ステートメントは、MDX スクリプト定義内でのみ使用できます。「 [MdxScript 要素 &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/objects/mdxscript-element-assl)」を参照してください。  
  
 また、1つのクエリで使用するために、計算されるメンバーを定義することもできます。 1 つのクエリに限定される計算されるメンバーを定義するには、SELECT ステートメントで WITH 句を使用します。 詳細については、「 [MDX でのメジャーの作成](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-building-measures)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Mdx&#41;&#40;mdx データ定義ステートメント](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
