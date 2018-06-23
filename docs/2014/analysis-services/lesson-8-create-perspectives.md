---
title: 'レッスン 9: パースペクティブの作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55b0f0d0-1cdf-4876-9c3d-d0c848be3f5d
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.openlocfilehash: fe2e746ec290aeb3b8690f818875616f2b9dd2f1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175842"
---
# <a name="lesson-9-create-perspectives"></a>レッスン 9: パースペクティブの作成
  このレッスンでは、Internet Sales パースペクティブを作成します。 パースペクティブとは、モデルの一部を表示可能なサブセットとして定義するものです。これにより、ビジネス固有またはアプリケーション固有のビューポイントを的を絞って作成できます。 パースペクティブを使用してモデルに接続すると、そのパースペクティブ内に定義されたモデル オブジェクト (テーブル、列、メジャー、階層、および KPI) のみがフィールドとして表示されます。  
  
 このレッスンで作成する Internet Sales パースペクティブでは、Customer テーブル オブジェクトが除外されます。 特定のオブジェクトをビューから除外するパースペクティブを作成した場合、そのオブジェクトはモデル内に依然として存在しますが、レポート クライアントのフィールドの一覧には表示されなくなります。 計算列とメジャーは、パースペクティブに含まれているかどうかに関係なく、除外されたデータ オブジェクトに基づく計算を引き続き実行できます。  
  
 このレッスンの目的は、パースペクティブの作成方法を知ることと、テーブル モデル作成ツールに慣れることです。 後でこのモデルにテーブルを追加する場合は、追加のパースペクティブを作成して、モデルに対する異なるビューポイント (Inventory や Sales Force など) を定義できます。  
  
 詳細については、「[パースペクティブ (SSAS テーブル)](tabular-models/perspectives-ssas-tabular.md)」を参照してください。  
  
 このレッスンの推定所要時間: **5 分**  
  
## <a name="prerequisites"></a>前提条件  
 このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン「[レッスン 8: 主要業績評価指標の作成](lesson-7-create-key-performance-indicators.md)」を完了している必要があります。  
  
## <a name="create-perspectives"></a>パースペクティブを作成する  
  
#### <a name="to-create-an-internet-sales-perspective"></a>Internet Sales パースペクティブを作成するには  
  
1.  モデル デザイナーで、をクリックして、**モデル** メニューをクリックして**パースペクティブ**です。  
  
2.  **[パースペクティブ]** ダイアログ ボックスで、 **[新しいパースペクティブ]** をクリックします。  
  
3.  パースペクティブの名前を変更するにはダブルクリック、**新しいパースペクティブ 1**列見出し、および入力`Internet Sales`です。  
  
4.  **フィールド**、次のテーブルの選択**日付**、 **Geography**、**製品**、 **Product Category**、 **Product Subcategory**、および`Internet Sales`です。  
  
     Customer テーブルおよびそのすべての列をこのパースペクティブから除外したことに注意してください。 後ほど、レッスン 12 で、"Excel で分析" 機能を使用してこのパースペクティブをテストします。 Excel ピボットテーブルのフィールドの一覧には、Customer テーブルを除く各テーブルが含まれます。  
  
5.  選択内容を確認し、 **Customer** テーブルがオフになっていることを確認して、 **[OK]** をクリックします。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルを続行するには、次のレッスン「[レッスン 10: 階層の作成](lesson-9-create-hierarchies.md)」に進んでください。  
  
  