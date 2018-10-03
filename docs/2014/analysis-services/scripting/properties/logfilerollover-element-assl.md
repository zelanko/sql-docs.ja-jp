---
title: LogFileRollover 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- LogFileRollover Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- LogFileRollover
helpviewer_keywords:
- LogFileRollover element
ms.assetid: 5484e167-b891-431a-bbae-946ea6eb4a3c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4c9c07dd08cacfbc273f2b0e691b178d4953ce42
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054852"
---
# <a name="logfilerollover-element-assl"></a>LogFileRollover 要素 (ASSL)
  指定のログ記録するかどうか[トレース](../objects/trace-element-assl.md)出力は、新しいファイルにロール オーバーする必要がありますまたはで指定されている最大ログ ファイル サイズときに停止してください[LogFileSize](logfilesize-element-assl.md)に到達します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Trace>  
   ...  
   <LogFileRollover>...</LogFileRollover>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|False|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[トレース](../objects/trace-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `LogFileRollover` 要素の値が True に設定されている場合は、ログ ファイルのサイズが `LogFileSize` 親要素の `Trace` 要素で指定された値を超えると、新しいファイルが開始されます。それ以外の場合は、ログ記録が停止されます。  
  
 親に対応する要素`LogFileRollover`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Trace>します。  
  
## <a name="see-also"></a>参照  
 [要素をトレース&#40;ASSL&#41;](../collections/traces-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
