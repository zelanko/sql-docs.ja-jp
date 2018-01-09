---
title: "Isolation 要素 (ASSL) |Microsoft ドキュメント"
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
apiname: Isolation Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: Isolation element
ms.assetid: 28c98c6f-668e-4547-8d25-127cc3995a7d
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fcfea788dfb2928b9c92037e845613fee873c994
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="isolation-element-assl"></a>Isolation 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]派生した要素の分離レベルを示す、[データソース](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md)データ型。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DataSource>  
   ...  
   <Isolation>...</Isolation>  
   ...  
</DataSource>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*ReadCommitted*|  
|基数|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[データ ソース](../../../analysis-services/scripting/data-type/datasource-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表に、文字列の 1 つに制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|*ReadCommitted*|他のトランザクションで変更されたが、まだコミットされていないデータを、ステートメントで読み取れないように指定します。 これにより、ダーティ リードを防ぐことができます。 他のトランザクションは、現在のトランザクション内の個々のステートメント間でデータを変更できます。 この結果、反復不能読み取りまたはファントム データが発生します。 この値は、既定値を**分離**要素。|  
|*スナップショット*|トランザクションの任意のステートメントによって読み取られるデータは、トランザクションの開始時に存在していたデータのバージョンとトランザクション的な一貫性があることを指定します。 トランザクションでは、トランザクションの開始前にコミットされたデータの変更のみを認識できます。 現在のトランザクションの開始後に他のトランザクションによって行われたデータの変更は、現在のトランザクションを実行しているステートメントでは認識できません。 このオプションでは、トランザクションの各ステートメントにおいて、トランザクションの開始時点でコミットされていたデータのスナップショットを取得するのと同じ効果が得られます。|  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
