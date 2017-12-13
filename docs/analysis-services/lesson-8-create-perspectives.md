---
title: "レッスン 9 パースペクティブの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/27/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: 55b0f0d0-1cdf-4876-9c3d-d0c848be3f5d
caps.latest.revision: "23"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 1b024c48c9a033f65804c3cfe67a518f436052b7
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="lesson-8-create-perspectives"></a>レッスン 8: パースペクティブを作成します。
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンでは、Internet Sales パースペクティブを作成します。 パースペクティブとは、モデルの一部を表示可能なサブセットとして定義するものです。これにより、ビジネス固有またはアプリケーション固有のビューポイントを的を絞って作成できます。 ユーザーは、パースペクティブを使用して、モデルに接続、モデル オブジェクトのみ (テーブル、列、メジャー、階層、および Kpi) そのパースペクティブで定義されたフィールドとして表示されます。  
  
このレッスンで作成する Internet Sales パースペクティブでは、DimCustomer テーブル オブジェクトを除外します。 特定のオブジェクトをビューから除外するパースペクティブを作成した場合、そのオブジェクトはモデル内に依然として存在しますが、レポート クライアントのフィールドの一覧には表示されなくなります。 計算列とメジャーは、パースペクティブに含まれているかどうかに関係なく、除外されたデータ オブジェクトに基づく計算を引き続き実行できます。  
  
このレッスンの目的は、パースペクティブの作成方法を知ることと、テーブル モデル作成ツールに慣れることです。 後でこのモデルに追加のテーブルを展開する場合は、モデルの在庫および販売などの別のビュー ポイントを定義する追加のパースペクティブを作成できます。 詳細については、「 [[パースペクティブ]](../analysis-services/tabular-models/perspectives-ssas-tabular.md)」を参照してください。  
  
このレッスンの推定所要時間: **5 分**  
  
## <a name="prerequisites"></a>前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 7: 主要業績評価指標の作成](../analysis-services/lesson-7-create-key-performance-indicators.md)です。  
  
## <a name="create-perspectives"></a>パースペクティブを作成する  
  
#### <a name="to-create-an-internet-sales-perspective"></a>Internet Sales パースペクティブを作成するには  
  
1.  クリックして、**モデル**メニュー >**パースペクティブ** > **の作成と管理**です。  
  
2.  **[パースペクティブ]** ダイアログ ボックスで、 **[新しいパースペクティブ]**をクリックします。  
  
3.  ダブルクリックして、**新しいパースペクティブ**列見出し、および名前の変更**Internet Sales**です。  
  
4.  すべてのテーブルを選択して*を除く* **DimCustomer**です。  
  
    ![として-表形式の lesson8-パースペクティブ](../analysis-services/media/as-tabular-lesson8-perspectives.png)
  
    後のレッスンでは Excel の機能で、分析を使用してこのパースペクティブをテストします。 Excel のピボット テーブル フィールド リストでは、DimCustomer テーブルを除く各テーブルが含まれます。  

## <a name="whats-next"></a>次の操作
次のレッスンに移動:[レッスン 9: 階層の作成](../analysis-services/lesson-9-create-hierarchies.md)です。
  
  
  
  
