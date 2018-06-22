---
title: '[全般] ([パーティションのプロパティ] ダイアログ ボックス) (SSMS) |Microsoft ドキュメント'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.sqlserverstudio.partitionproperties.general.f1
ms.assetid: efb505be-354f-4d23-8f2d-3e76fa50d27b
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 0008344f56afefca65c9c94b1b4446b5d84455dd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074701"
---
# <a name="general-partition-properties-dialog-box-ssms"></a>[全般] ([パーティションのプロパティ] ダイアログ ボックス) (SSMS)
  SQL Server Management Studio の **[パーティションのプロパティ]** ダイアログ ボックスの **[全般]** ページを使用すると、[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースのキューブに対してメジャー グループのパーティションの全般プロパティを設定できます。  
  
## <a name="options"></a>および  
  
|項目|定義|  
|----------|----------------|  
|**集計デザイン ID**|パーティションによって使用される集計デザインの識別子を表示します。|  
|**集計プレフィックス**|パーティションによって含まれる集計インスタンスの既定のプレフィックスを表示します。|  
|**[タイムスタンプの作成]**|パーティションが作成された日時を表示します。|  
|**現在のストレージ モード**|パーティションの現在のストレージ モードを表示します。<br /><br /> 注: このモードは、パーティションのプロアクティブ キャッシュ設定によって異なる場合があります。 プロアクティブ キャッシュの詳細については、「[プロアクティブ キャッシュ (パーティション)](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)」をご覧ください。|  
|**description**|変更するパーティションの説明を入力します。|  
|**推定行数**|パーティションによって表示される、基となるデータ ソース内の予測行数を入力します。 この値は、パーティション処理にかかる時間と要求されるストレージを予測するために、処理中に使用されます。|  
|**サイズの見積もり**|パーティションの推定サイズを表示します。|  
|**ID**|パーティションの識別子を表示します。|  
|**最後に処理されました。**|パーティションが最終処理された日時を表示します。|  
|**[スキーマの最終更新]**|パーティションのメタデータが最後に更新された日時を表示します。|  
|**Name**|パーティションの名前が表示されます。|  
|**処理モード**|パーティションの処理モードを選択します。 処理モードの詳細については[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、オブジェクトを参照してください[多次元モデル オブジェクトの処理](multidimensional-models/processing-a-multidimensional-model-analysis-services.md)です。|  
|**リモート データ ソース ID**|パーティションのソース データの取得元となるリモート データ ソースの識別子を表示します。<br /><br /> 注: このプロパティには、リモート パーティションの値のみが含まれます。|  
|**スライス**|パーティションによって表示されるデータ スライスを識別する式を表示します。|  
|**Source**|パーティションにソース データを提供するテーブルまたはクエリを表示します。|  
|**State**|パーティションの現在の処理状態を表示します。|  
|**記憶域の場所**|パーティションのデータが格納されるフォルダーを表示します。<br /><br /> 注: このプロパティには、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスの既定以外の場所にストレージの場所が指定されている場合にのみ、値が示されます。|  
|**Type**|パーティションの種類を表示します。|  
  
## <a name="see-also"></a>参照  
 [パーティション&#40;Analysis Services - 多次元データ&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)   
 [リモート パーティション](multidimensional-models-olap-logical-cube-objects/partitions-remote-partitions.md)   
 [パーティションのプロパティ ダイアログ ボックス&#40;SSMS&#41;](partition-properties-dialog-box-ssms.md)   
 [選択範囲&#40;プロパティ ダイアログ ボックスをパーティション分割&#41; &#40;SSMS&#41;](selection-partition-properties-dialog-box-ssms.md)   
 [プロアクティブ キャッシュ&#40;プロパティ ダイアログ ボックスをパーティション分割&#41; &#40;SSMS&#41;](proactive-caching-partition-properties-dialog-box-ssms.md)   
 [キューブ、パーティション、およびディメンションの処理のエラー構成&#40;SSAS - 多次元&#41;](multidimensional-models/error-configuration-for-cube-partition-and-dimension-processing.md)  
  
  