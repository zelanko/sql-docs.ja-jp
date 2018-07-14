---
title: KeyErrorLimitAction 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- KeyErrorLimitAction Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- KeyErrorLimitAction
helpviewer_keywords:
- KeyErrorLimitAction element
ms.assetid: a2a01aae-0571-499f-9025-b61c741f3ddb
caps.latest.revision: 35
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e6001901e7613099eff2856905b88452870f7f2d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37247272"
---
# <a name="keyerrorlimitaction-element-assl"></a>KeyErrorLimitAction 要素 (ASSL)
  アクションを指定[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]ときいるキー エラー数がで指定された、 [KeyErrorLimit](keyerrorlimit-element-assl.md)要素に到達します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <KeyErrorLimitAction>...</KeyErrorLimitAction>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*StopProcessing*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ErrorConfiguration](../objects/errorconfiguration-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|説明|  
|-----------|-----------------|  
|*StopProcessing*|オブジェクトの処理を停止します。|  
|*StopLogging*|オブジェクトの処理は継続されますが、処理中に発生したエラーのログ記録を停止します。|  
  
 許容された値に対応する列挙体`KeyErrorLimitAction`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.KeyErrorLimitAction>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
