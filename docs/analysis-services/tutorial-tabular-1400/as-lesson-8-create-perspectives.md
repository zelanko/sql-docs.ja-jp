---
title: 'Analysis Services のチュートリアル レッスン 8: パースペクティブを作成 |Microsoft Docs'
ms.date: 08/27/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 080b20dbcf7438d26102a3bf906256343271af45
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43085323"
---
# <a name="create-perspectives"></a>パースペクティブを作成する

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは、Internet Sales パースペクティブを作成します。 パースペクティブとは、モデルの一部を表示可能なサブセットとして定義するものです。これにより、ビジネス固有またはアプリケーション固有のビューポイントを的を絞って作成できます。 ユーザーは、パースペクティブを使用して、モデルに接続、モデル オブジェクトのみ (テーブル、列、メジャー、階層、および Kpi) そのパースペクティブで定義されているフィールドとして表示されます。 詳細についてを参照してください。[パースペクティブ](../tabular-models/perspectives-ssas-tabular.md)します。
  
このレッスンで作成する Internet Sales パースペクティブは、DimCustomer テーブル オブジェクトを除外します。 ビューから特定のオブジェクトを除外するパースペクティブを作成するときに、そのオブジェクトはまだモデルに存在します。 ただし、レポート クライアント フィールドの一覧に表示はされません。 計算列とメジャーは、パースペクティブに含まれているかどうかに関係なく、除外されたデータ オブジェクトに基づく計算を引き続き実行できます。  
  
このレッスンの目的は、パースペクティブの作成方法を知ることと、テーブル モデル作成ツールに慣れることです。 このモデルに追加のテーブルを後で展開する場合は、モデルの在庫および販売などの別のビュー ポイントを定義する追加のパースペクティブを作成できます。  
  
このレッスンを完了するまでに時間を推定: **5 分**  
  
## <a name="prerequisites"></a>Prerequisites  

この記事では、順序で完了する必要があります、表形式モデルのチュートリアルの一部です。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 7: 主要業績評価指標の作成](../tutorial-tabular-1400/as-lesson-7-create-key-performance-indicators.md)です。  
  
## <a name="create-perspectives"></a>パースペクティブを作成する  
  
#### <a name="to-create-an-internet-sales-perspective"></a>Internet Sales パースペクティブを作成するには  
  
1.  をクリックして、**モデル**メニュー >**パースペクティブ** > **作成と管理**します。  
  
2.  **[パースペクティブ]** ダイアログ ボックスで、 **[新しいパースペクティブ]** をクリックします。  
  
3.  ダブルクリックして、**新しいパースペクティブ**列見出し、および名前の変更**Internet Sales**します。  
  
4.  すべてのテーブルを選択する*を除く* **DimCustomer**します。  
  
    ![lesson8-パースペクティブとして](../tutorial-tabular-1400/media/as-lesson8-perspectives.png)
  
    後のレッスンではこのパースペクティブをテストするのに in Excel 機能、分析を使用します。 Excel のピボット テーブル フィールド リストには、DimCustomer テーブルを除く各テーブルが含まれています。  

## <a name="whats-next"></a>次の操作

[レッスン 9: 階層を作成する](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md)します。
  
  
  
  
