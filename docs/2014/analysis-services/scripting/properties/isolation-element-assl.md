---
title: Isolation 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Isolation Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Isolation element
ms.assetid: 28c98c6f-668e-4547-8d25-127cc3995a7d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 23abd455717c5eb6ae9e32c4ad9309e52f3841e7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48121362"
---
# <a name="isolation-element-assl"></a>Isolation 要素 (ASSL)
  派生した要素の分離レベルを示します、 [DataSource](../data-type/datasource-data-type-assl.md)データ型。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DataSource>  
   ...  
   <Isolation>...</Isolation>  
   ...  
</DataSource>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*ReadCommitted*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[DataSource](../data-type/datasource-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表に、文字列の 1 つに制限されます。  
  
|値|説明|  
|-----------|-----------------|  
|*ReadCommitted*|他のトランザクションで変更されたが、まだコミットされていないデータを、ステートメントで読み取れないように指定します。 これにより、ダーティ リードを防ぐことができます。 他のトランザクションは、現在のトランザクション内の個々のステートメント間でデータを変更できます。 この結果、反復不能読み取りまたはファントム データが発生します。 この値は `Isolation` 要素の既定値です。|  
|*スナップショット*|トランザクションの任意のステートメントによって読み取られるデータは、トランザクションの開始時に存在していたデータのバージョンとトランザクション的な一貫性があることを指定します。 トランザクションでは、トランザクションの開始前にコミットされたデータの変更のみを認識できます。 現在のトランザクションの開始後に他のトランザクションによって行われたデータの変更は、現在のトランザクションを実行しているステートメントでは認識できません。 このオプションでは、トランザクションの各ステートメントにおいて、トランザクションの開始時点でコミットされていたデータのスナップショットを取得するのと同じ効果が得られます。|  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
