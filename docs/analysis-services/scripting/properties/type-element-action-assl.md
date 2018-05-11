---
title: Type 要素 (アクション) (ASSL) |Microsoft ドキュメント
ms.date: 5/8/2018
ms.prod: sql
ms.component: assl
ms.reviewer: owend
ms.technology: analysis-services
ms.topic: reference
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a82395be70c699da6fc96d3661aa71254e185883
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="type-element-action-assl"></a>Type 要素 (アクション) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
|*Statement*|OLE DB コマンドを実行します。|  
|*ドリル スルー*|ドリルスルーの行セットを取得します。<br /><br /> この値は*行セット*し、ドリルスルー アクションを識別します。 のみを指定できますがアクションで使用される[TargetType](../../../analysis-services/scripting/properties/targettype-element-assl.md)に値が設定されている*セル*です。|  
|*データセット*|データセットを取得します。|  
|*行セット*|行セットを取得します。|  
|*コマンドライン*|コマンド プロンプトでコマンドを実行します。|  
|*独自*|上記以外のインターフェイスを使用して操作を実行します。|  
|*レポート*|インターネット ブラウザーで変数ページを表示します。<br /><br /> この値は*Url*し、レポートの操作を識別します。|  
  
 親に対応する要素**型**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Action>します。  
  
## <a name="see-also"></a>参照  
 [DrillThroughAction データ型&#40;ASSL&#41;](../../../analysis-services/scripting/data-type/drillthroughaction-data-type-assl.md)   
 [ReportAction データ型&#40;ASSL&#41;](../../../analysis-services/scripting/data-type/reportaction-data-type-assl.md)   
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
