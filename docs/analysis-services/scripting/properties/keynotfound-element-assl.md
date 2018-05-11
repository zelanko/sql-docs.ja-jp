---
title: KeyNotFound 要素 (ASSL) |Microsoft ドキュメント
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e90452cb0b40dac2ce285cf0058ed820bff9c0dd
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="keynotfound-element-assl"></a>KeyNotFound 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  指定方法[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]参照整合性エラーが発生したときに応答します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ErrorConfiguration>  
   ...  
      <KeyNotFound>...</KeyNotFound>  
   ...  
</ErrorConfiguration>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*[ReportAndContinue]*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
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
|*[ReportAndContinue]*|エラーを報告し、処理を続行します。|  
|*ReportAndStop*|エラーを報告し、処理を停止します。|  
  
 許可される値に対応する列挙**KeyNotFound**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ErrorOption>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
