---
title: '&lt;= (に等しいまたはそれよりも小さい) (DMX) |Microsoft Docs'
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 12dc7ca07dba7d36e7f65c9c6097b8b42457d3da
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62503042"
---
# <a name="lt-less-than-or-equal-to-dmx"></a>&lt;= (に等しいまたはそれよりも小さい) (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  あるデータ マイニング拡張機能 (DMX) 式の値が他の DMX 式の値以下かどうかを判断する比較演算子を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
DMX_Expression <= DMX_Expression  
```  
  
#### <a name="parameters"></a>パラメーター  
 *DMX_Expression*  
 有効な DMX 式です。  
  
## <a name="return-value"></a>戻り値  
 両方のパラメーターが null 以外の場合、TRUE を含むブール値と最初のパラメーターの値は、2 番目のパラメーターの値に等しいまたはそれよりも小さいです。 ブール値には、両方のパラメーターが null でないと、最初のパラメーターの値が 2 番目のパラメーターの値より大きい場合は FALSE が含まれています。 ブール値には、いずれかまたは両方のパラメーターが null 値に評価される場合、null 値が含まれています。  
  
## <a name="see-also"></a>参照  
 [比較演算子&#40;DMX&#41;](../dmx/operators-comparison.md)   
 [データ マイニング拡張機能&#40;DMX&#41;演算子リファレンス](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [演算子&#40;DMX&#41;](../dmx/operators-dmx.md)  
  
  
