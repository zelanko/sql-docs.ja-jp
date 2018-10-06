---
title: DAX のプロパティ |Microsoft Docs
ms.date: 10/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 794caf245e0cc3494713991159c5a911a187afae
ms.sourcegitcommit: 448106b618fe243e418bbfc3daae7aee8d8553d2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/04/2018
ms.locfileid: "48264868"
---
# <a name="dax-properties"></a>DAX のプロパティ
[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

   Msmdsrv.ini の DAX セクションには、DAX クエリの結果セットで返される行の数の上限など、Analysis Services では、特定のクエリの動作の制御に使用される設定が含まれています。

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

設定 |値 |説明
--------|-------|-----------
MaxIntermediateRowsetSize | 1000000 | DAX クエリで返される最大行数。 既定値が小さすぎる場合は、このエントリを手動で msmdsrv.ini ファイルに追加し、値を増やします。
PredicateCheckSpoolCardinalityThreshold| 5000 | 高度なプロパティであるため、マイクロソフトのサポート下でのみ変更してください。

その他のサーバー プロパティとその設定方法の詳細については、「 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)」を参照してください。
