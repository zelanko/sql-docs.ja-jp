---
title: "KeyNotFound 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: KeyNotFound Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: KeyNotFound
helpviewer_keywords: KeyNotFound element
ms.assetid: 2a93bbfa-2409-4e94-8b68-926532895a4c
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 387e6fe29fb01be462350c0d79d63e450e9b1125
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="keynotfound-element-assl"></a>KeyNotFound 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]指定方法[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]参照整合性エラーが発生したときに応答します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <KeyNotFound>...</KeyNotFound>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*[Reportandcontinue]*|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 参照整合性エラーは、従属テーブル内の外部キー値に対応するエントリが親テーブルに存在しない場合に発生します。 このエラーは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] によって処理されたディメンション内のファクト テーブルが、そのディメンションのディメンション テーブルに存在しない外部キー値を参照している場合や、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] によって処理されたパーティションに含まれているディメンションのディメンション メイン テーブルが、別の関連するディメンション テーブルに存在しないキー値を参照している場合に発生します  (親子階層および親属性を持つディメンションの場合は、パーティションに含まれているディメンションのディメンション メイン テーブルが、同じディメンション テーブルに存在しないキー値を参照しているときにも発生します)。  
  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|*IgnoreError*|エラーを無視し、処理を続行します。|  
|*[Reportandcontinue]*|エラーを報告し、処理を続行します。|  
|*ReportAndStop*|エラーを報告し、処理を停止します。|  
  
 許可される値に対応する列挙**KeyNotFound**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ErrorOption>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
