---
title: "Type 要素 (アクション) (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
apiname: Type Element (Action)
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: TYPE
helpviewer_keywords: Type element
ms.assetid: 534cdf99-1edf-4490-9eaa-61f189a19434
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3a84623ef5ee2b870e767217ae5f8664ac44d517
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="type-element-action-assl"></a>Type 要素 (アクション) (ASSL)
  型を含む、[アクション](../../../analysis-services/scripting/objects/action-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Action>  
   ...  
   <Type>...</Type>  
   ...  
</Action>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[操作](../../../analysis-services/scripting/objects/action-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*Url*|インターネット ブラウザーで変数ページを表示します。|  
|*Html*|インターネット ブラウザーで HTML スクリプトを実行します。|  
|*ステートメント*|OLE DB コマンドを実行します。|  
|*ドリル スルー*|ドリルスルーの行セットを取得します。<br /><br /> この値は*行セット*し、ドリルスルー アクションを識別します。 のみを指定できますがアクションで使用される[TargetType](../../../analysis-services/scripting/properties/targettype-element-assl.md)に値が設定されている*セル*です。|  
|*データセット*|データセットを取得します。|  
|*行セット*|行セットを取得します。|  
|*コマンドライン*|コマンド プロンプトでコマンドを実行します。|  
|*独自*|上記以外のインターフェイスを使用して操作を実行します。|  
|*レポート*|インターネット ブラウザーで変数ページを表示します。<br /><br /> この値は*Url*し、レポートの操作を識別します。|  
  
 親に対応する要素**型**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Action>します。  
  
## <a name="see-also"></a>参照  
 [DrillThroughAction データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)   
 [ReportAction データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)   
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
