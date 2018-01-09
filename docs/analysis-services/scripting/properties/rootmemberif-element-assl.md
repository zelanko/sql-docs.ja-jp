---
title: "RootMemberIf 要素 (ASSL) |Microsoft ドキュメント"
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
apiname: RootMemberIf Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: RootMemberIf
helpviewer_keywords: RootMemberIf element
ms.assetid: b695e271-c748-4abc-a09f-acb1014f768f
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: c5a3a75efa13710bcc00a94ed55cee407dbbbc8d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="rootmemberif-element-assl"></a>RootMemberIf 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]ルート メンバーまたは親属性のメンバーを識別する方法を決定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute>  
   ...  
   <RootMemberIf>...</RootMemberIf>  
   ...  
</DimensionAttribute>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*ParentIsBlankSelfOrMissing*|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DimensionAttribute](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 値、 **RootMemberIf**要素は親属性によってのみ使用 (つまり、他の値、[使用状況](../../../analysis-services/scripting/properties/usage-element-dimensionattribute-assl.md)の要素、 **DimensionAttribute**親要素設定*親*)、親子階層のルート (最上位) メンバーを判断します。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*ParentIsBlankSelfOrMissing*|説明の条件の 1 つ以上満たすメンバーだけ*ParentIsBlank*、 *ParentIsSelf*、または*ParentIsMissing*ルート メンバーとして扱われます。|  
|*ParentIsBlank*|Null、0、または空の文字列で表されるキー列でのメンバーのみ、 [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md)のコレクション**DimensionAttribute**ルート メンバーとして扱われます。|  
|*ParentIsSelf*|自分自身が親であるメンバーのみがルート メンバーとして扱われます。|  
|*ParentIsMissing*|親が見つからないメンバーのみがルート メンバーとして扱われます。|  
  
 許可される値に対応する列挙**RootMemberIf**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.RootIfValue>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
