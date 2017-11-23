---
title: "KeyErrorAction 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: KeyErrorAction Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: KeyErrorAction
helpviewer_keywords: KeyErrorAction element
ms.assetid: 91fa9f88-b79e-4996-9717-d7ca82b64ddd
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bce4f3cad46fd15fbdde64d1697429aaf229ff9c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="keyerroraction-element-assl"></a>KeyErrorAction 要素 (ASSL)
  アクションを指定[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]キーでエラーが発生したときに実行します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <KeyErrorAction>...</KeyErrorAction>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*ConvertToUnknown*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*ConvertToUnknown*|問題のキーを不明なメンバー値に変換します。|  
|*DiscardRecord*|レコードを破棄します。|  
  
 許可される値に対応する列挙**KeyErrorAction**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.KeyErrorAction>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
