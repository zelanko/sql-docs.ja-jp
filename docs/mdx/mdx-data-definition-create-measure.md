---
title: CREATE MEASURE ステートメント (MDX) |Microsoft ドキュメント
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
ms.assetid: f264ba96-cbbe-488b-8ac9-b3056a6e997b
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: c87b1b725489de8b163ab5a2a7d73794eddce9e9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-data-definition---create-measure"></a>MDX データ定義のメジャーを作成します。
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  テーブル モデルでメジャーを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
CREATE MEASURE Table_Name[Measure_Name] = DAX_Expression  
[; CREATE MEASURE ...n]  
  
```  
  
## <a name="arguments"></a>引数  
 *Table_Name*  
 メジャーを作成するテーブルの名前を指定する有効な文字列リテラルです。  
  
 *Measure_Name*  
 メジャー名を指定する有効な文字列リテラルです。  
  
 *DAX_Expression*  
 1 つのスカラー値を返す有効な DAX 式を入力します。  
  
## <a name="remarks"></a>解説  
 *Measure_Name*角かっこで囲む必要があります。  
  
 CREATE MEASURE ステートメントは、MDX スクリプトの定義です。 内部でのみ使用できます。参照してください[MdxScript 要素&#40;ASSL&#41;](../analysis-services/scripting/objects/mdxscript-element-assl.md)です。  
  
 1 つのクエリだけで使用する計算されるメンバーを定義することも可能です。 1 つのクエリに限定される計算されるメンバーを定義するには、SELECT ステートメントで WITH 句を使用します。 詳細については、次を参照してください。 [MDX でのメジャーの作成](../analysis-services/multidimensional-models/mdx/mdx-building-measures.md)です。  
  
## <a name="see-also"></a>参照  
 [MDX データ定義ステートメント&#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
