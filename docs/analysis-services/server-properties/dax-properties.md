---
title: Analysis Services DAX のプロパティ |Microsoft Docs
ms.date: 10/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 20a6df833f8c525c24abdf3bb51278d0067db951
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62509658"
---
# <a name="dax-properties"></a>DAX のプロパティ
[!INCLUDE[ssas-appliesto-sqlas-all](../../includes/ssas-appliesto-sqlas-all.md)]

   Msmdsrv.ini の DAX セクションには、DAX クエリの結果セットで返される行の数の上限など、Analysis Services では、特定のクエリの動作の制御に使用される設定が含まれています。

  巨大な行セットについては、DirectQuery モデルで返される行数など、既定の 100 万行では不十分である場合があります。 制限によって、このエラーが発生した場合の調整が必要かどうかがわかります。「外部データ ソースへのクエリの結果セットを超えました '1000000' 行のサイズが最大。」

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
