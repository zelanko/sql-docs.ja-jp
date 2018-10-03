---
title: Type 要素 (アクション) (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Type Element (Action)
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- TYPE
helpviewer_keywords:
- Type element
ms.assetid: 534cdf99-1edf-4490-9eaa-61f189a19434
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: af38eb6a60e8e54ecfc4ac5bb4fb05faeab69feb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48168422"
---
# <a name="type-element-action-assl"></a>Type 要素 (アクション) (ASSL)
  型を含む、[アクション](../objects/action-element-assl.md)要素。  
  
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
|親要素|[操作](../objects/action-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*Url*|インターネット ブラウザーで変数ページを表示します。|  
|*Html*|インターネット ブラウザーで HTML スクリプトを実行します。|  
|*ステートメント*|OLE DB コマンドを実行します。|  
|*ドリル スルー*|ドリルスルーの行セットを取得します。<br /><br /> この値は*行セット*ドリルスルー アクションを識別します。 できますのみがアクションで使用される[TargetType](targettype-element-assl.md)値に設定されて*セル*。|  
|*データセット*|データセットを取得します。|  
|*行セット*|行セットを取得します。|  
|*コマンドライン*|コマンド プロンプトでコマンドを実行します。|  
|*独自*|上記以外のインターフェイスを使用して操作を実行します。|  
|*レポート*|インターネット ブラウザーで変数ページを表示します。<br /><br /> この値は*Url*レポート アクションを識別します。|  
  
 親に対応する要素`Type`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Action>します。  
  
## <a name="see-also"></a>参照  
 [DrillThroughAction データ型&#40;ASSL&#41;](../data-type/action-data-type-assl.md)   
 [ReportAction データ型&#40;ASSL&#41;](../data-type/reportaction-data-type-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
