---
title: LogFileRollover 要素 (ASSL) |Microsoft ドキュメント
ms.date: 5/8/2018
ms.prod: sql
ms.custom: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 73762fbfb606067d7f90beb2b11364d9e8dd0b4d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="logfilerollover-element-assl"></a>LogFileRollover 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  指定のログ記録するかどうか[トレース](../../../analysis-services/scripting/objects/trace-element-assl.md)出力は新しいファイルにロール オーバーするかまたは停止されている最大ログ ファイル サイズとがで指定する必要があります[LogFileSize](../../../analysis-services/scripting/properties/logfilesize-element-assl.md)に到達します。  
  
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
|親要素|[トレース](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **LogFileRollover** 要素の値が True に設定されている場合は、ログ ファイルのサイズが **LogFileSize** 親要素の **Trace** 要素で指定された値を超えると、新しいファイルが開始されます。それ以外の場合は、ログ記録が停止されます。  
  
 親に対応する要素**LogFileRollover**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Trace>します。  
  
## <a name="see-also"></a>参照  
 [Traces 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/collections/traces-element-assl.md)   
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
