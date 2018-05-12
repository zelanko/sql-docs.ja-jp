---
title: FORE_COLOR および BACK_COLOR の内容 (MDX) |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bb721d04e32e584a312c779db3aadab2ab83ba19
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="mdx-cell-properties---forecolor-and-backcolor-contents"></a>MDX のセルのプロパティ - FORE_COLOR および BACK_COLOR の内容
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  セル プロパティ **FORE_COLOR** および **BACK_COLOR** は、セルのテキストの色および背景色についての情報を Microsoft Windows オペレーティング システムの赤緑青 (RGB) 形式で格納します。  
  
 通常の RGB 色の有効範囲は 0 ～ 16,777,215 (&H00FFFFFF) です。 この範囲の高位バイトは常に 0 で、最も低いバイトから意味を成すバイトまでの下位 3 バイトによって、赤、緑、および青それぞれの量が決まります。 赤、緑、および青のコンポーネントは、それぞれ 0 ～ 255 (&HFF) までの数値で表されます。  
  
## <a name="see-also"></a>参照  
 [セルのプロパティ & #40; を使用します。MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md)  
  
  
