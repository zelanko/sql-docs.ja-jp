---
title: レッスン 8 パースペクティブの作成 |Microsoft Docs
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5f68e51be75e84226dd0b1fd3e578fa4031eda04
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65403524"
---
# <a name="lesson-8-create-perspectives"></a>レッスン 8: パースペクティブを作成する
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンでは、Internet Sales パースペクティブを作成します。 パースペクティブとは、モデルの一部を表示可能なサブセットとして定義するものです。これにより、ビジネス固有またはアプリケーション固有のビューポイントを的を絞って作成できます。 ユーザーは、パースペクティブを使用して、モデルに接続、モデル オブジェクトのみ (テーブル、列、メジャー、階層、および Kpi) そのパースペクティブで定義されているフィールドとして表示されます。  
  
このレッスンで作成する Internet Sales パースペクティブは、DimCustomer テーブル オブジェクトを除外します。 特定のオブジェクトをビューから除外するパースペクティブを作成した場合、そのオブジェクトはモデル内に依然として存在しますが、レポート クライアントのフィールドの一覧には表示されなくなります。 計算列とメジャーは、パースペクティブに含まれているかどうかに関係なく、除外されたデータ オブジェクトに基づく計算を引き続き実行できます。  
  
このレッスンの目的は、パースペクティブの作成方法を知ることと、テーブル モデル作成ツールに慣れることです。 このモデルに追加のテーブルを後で展開する場合は、モデルの在庫および販売などの別のビュー ポイントを定義する追加のパースペクティブを作成できます。 詳細については、「 [[パースペクティブ]](../tabular-models/perspectives-ssas-tabular.md)」を参照してください。  
  
このレッスンを完了するまでに時間を推定するには。**5 分**  
  
## <a name="prerequisites"></a>前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に、前のレッスンを完了が必要があります。[レッスン 7: 主要業績評価指標の作成](lesson-7-create-key-performance-indicators.md)です。  
  
## <a name="create-perspectives"></a>パースペクティブを作成する  
  
#### <a name="to-create-an-internet-sales-perspective"></a>Internet Sales パースペクティブを作成するには  
  
1.  をクリックして、**モデル**メニュー >**パースペクティブ** > **作成と管理**します。  
  
2.  **[パースペクティブ]** ダイアログ ボックスで、 **[新しいパースペクティブ]** をクリックします。  
  
3.  ダブルクリックして、**新しいパースペクティブ**列見出し、および名前の変更**Internet Sales**します。  
  
4.  すべてのテーブルを選択します。*を除く* **DimCustomer**します。  
  
    ![として-テーブル-lesson8-パースペクティブ](media/as-tabular-lesson8-perspectives.png)
  
    後のレッスンでは in Excel 機能、分析を使用してこのパースペクティブをテストします。 Excel のピボット テーブル フィールド リストでは、DimCustomer テーブルを除く各テーブルが含まれます。  

## <a name="whats-next"></a>次の操作
次のレッスンに移動します。[レッスン 9:階層を作成する](lesson-9-create-hierarchies.md)します。
  
  
  
  
