---
title: Analysis Services のチュートリアル レッスン 8 作成パースペクティブ |Microsoft ドキュメント
description: Analysis Services tutorial プロジェクトでパースペクティブを作成する方法について説明します。
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: ''
author: Minewiskan
manager: kfile
editor: ''
tags: ''
ms.assetid: ''
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: na
ms.date: 02/20/2018
ms.author: owend
monikerRange: '>= sql-analysis-services-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 7b6d5dd474719f33d285ac04f1643f330a618a7a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="create-perspectives"></a>パースペクティブを作成する

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンでは、Internet Sales パースペクティブを作成します。 パースペクティブとは、モデルの一部を表示可能なサブセットとして定義するものです。これにより、ビジネス固有またはアプリケーション固有のビューポイントを的を絞って作成できます。 ユーザーは、パースペクティブを使用して、モデルに接続、モデル オブジェクトのみ (テーブル、列、メジャー、階層、および Kpi) そのパースペクティブで定義されたフィールドとして表示されます。 詳細については、次を参照してください。[パースペクティブ](../tabular-models/perspectives-ssas-tabular.md)です。
  
このレッスンで作成する Internet Sales パースペクティブでは、DimCustomer テーブル オブジェクトを除外します。 ビューから特定のオブジェクトを除外するパースペクティブを作成するときに、そのオブジェクトはまだモデルに存在します。 ただし、レポート クライアント フィールドの一覧に表示はされません。 計算列とメジャーは、パースペクティブに含まれているかどうかに関係なく、除外されたデータ オブジェクトに基づく計算を引き続き実行できます。  
  
このレッスンの目的は、パースペクティブの作成方法を知ることと、テーブル モデル作成ツールに慣れることです。 後でこのモデルに追加のテーブルを展開する場合は、モデルの在庫および販売などの別のビュー ポイントを定義する追加のパースペクティブを作成できます。  
  
このレッスンを完了する時間を推定: **5 分**  
  
## <a name="prerequisites"></a>前提条件  

この記事は、順番に従って実行する必要がありますが、テーブル モデリング チュートリアルの一部です。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 7: 主要業績評価指標の作成](../tutorial-tabular-1400/as-lesson-7-create-key-performance-indicators.md)です。  
  
## <a name="create-perspectives"></a>パースペクティブを作成する  
  
#### <a name="to-create-an-internet-sales-perspective"></a>Internet Sales パースペクティブを作成するには  
  
1.  クリックして、**モデル**メニュー >**パースペクティブ** > **の作成と管理**です。  
  
2.  **[パースペクティブ]** ダイアログ ボックスで、 **[新しいパースペクティブ]**をクリックします。  
  
3.  ダブルクリックして、**新しいパースペクティブ**列見出し、および名前の変更**Internet Sales**です。  
  
4.  すべてのテーブル選択*を除く* **DimCustomer**です。  
  
    ![lesson8-パースペクティブとして](../tutorial-tabular-1400/media/as-lesson8-perspectives.png)
  
    後のレッスンではこのパースペクティブをテストするのに Excel の機能で分析を使用します。 Excel のピボット テーブル フィールド リストには、DimCustomer テーブルを除く各テーブルが含まれています。  

## <a name="whats-next"></a>次の操作

[レッスン 9: 階層を作成](../tutorial-tabular-1400/as-lesson-9-create-hierarchies.md)です。
  
  
  
  
