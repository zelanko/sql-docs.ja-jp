---
title: "LogFileRollover 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: LogFileRollover Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: LogFileRollover
helpviewer_keywords: LogFileRollover element
ms.assetid: 5484e167-b891-431a-bbae-946ea6eb4a3c
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 72dda45efc217f571969bb3354d5feb5bfa02604
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="logfilerollover-element-assl"></a>LogFileRollover 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]指定のログ記録するかどうか[トレース](../../../analysis-services/scripting/objects/trace-element-assl.md)出力は新しいファイルにロール オーバーするかまたは停止されている最大ログ ファイル サイズとがで指定する必要があります[LogFileSize](../../../analysis-services/scripting/properties/logfilesize-element-assl.md)に到達します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Trace>  
   ...  
   <LogFileRollover>...</LogFileRollover>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|False|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[トレース](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **LogFileRollover** 要素の値が True に設定されている場合は、ログ ファイルのサイズが **LogFileSize** 親要素の **Trace** 要素で指定された値を超えると、新しいファイルが開始されます。それ以外の場合は、ログ記録が停止されます。  
  
 親に対応する要素**LogFileRollover**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Trace>します。  
  
## <a name="see-also"></a>参照  
 [Traces 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/collections/traces-element-assl.md)   
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
