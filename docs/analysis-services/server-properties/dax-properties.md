---
title: "DAX プロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: aa928dc5-d00d-4f8a-80b9-7e6973d2196c
caps.latest.revision: "6"
author: HeidiSteen
ms.author: heidist
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 76ffc0da4e8d56b4bb37b0be5278e458ac6fb043
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="dax-properties"></a>DAX のプロパティ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Msmdsrv.ini の DAX セクションで特定のクエリの動作を制御するために使用する設定が含まれています。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、DAX クエリの結果セットで返される行の数の上限などです。 
  
  巨大な行セットについては、DirectQuery モデルで返される行数など、既定の 100 万行では不十分である場合があります。 上限の調整が必要であるかどうかは、"The result set of a query to external data source has exceeded the maximum allowed size of '1000000' rows (外部データ ソースへのクエリの結果セットが許可されている最大サイズである '1000000' 行を超えています)" というエラーが発生することでわかります。
 
上限を増やすには、 **MaxIntermediateRowSize** 構成設定を指定します。 構成ファイルの DAX セクションに全要素を手動で追加する必要があります。 追加するまで設定はファイル内に存在しません。
  
## <a name="configuration-snippet"></a>構成スニペット

```
<ConfigurationSettings>
. . .
<DAX>   
  <PredicateCheckSpoolCardinalityThreshold>5000
  </PredicateCheckSpoolCardinalityThreshold>
  <DQ>
     <MaxIntermediateRowsetSize>1000000
     </MaxIntermediateRowsetSize>
  </DQ>
</DAX>
. . . 
```

## <a name="property-descriptions"></a>プロパティの説明

設定 |値 |Description
--------|-------|-----------
MaxIntermediateRowsetSize | 1000000 | DAX クエリで返される最大行数。 既定値が小さすぎる場合は、このエントリを手動で msmdsrv.ini ファイルに追加し、値を増やします。 
PredicateCheckSpoolCardinalityThreshold| 5000 | 高度なプロパティであるため、マイクロソフトのサポート下でのみ変更してください。

その他のサーバー プロパティとその設定方法の詳細については、「 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)」を参照してください。 
