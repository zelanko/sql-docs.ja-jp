---
title: 'レッスン 9: パースペクティブの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 55b0f0d0-1cdf-4876-9c3d-d0c848be3f5d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bd395e605bfde9d34ed0dc4f16060812464efb56
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66078250"
---
# <a name="lesson-9-create-perspectives"></a>レッスン 9: パースペクティブの作成
  このレッスンでは、Internet Sales パースペクティブを作成します。 パースペクティブでは、表示可能なモデルのサブセットを定義して、集中的、ビジネス固有またはアプリケーション固有のビューポイントを作成できます。 パースペクティブを使用してモデルに接続すると、そのパースペクティブ内に定義されたモデル オブジェクト (テーブル、列、メジャー、階層、および KPI) のみがフィールドとして表示されます。  
  
 このレッスンで作成する Internet Sales パースペクティブでは、Customer テーブル オブジェクトが除外されます。 特定のオブジェクトをビューから除外するパースペクティブを作成しても、そのオブジェクトはまだモデルに存在します。ただし、レポートするクライアントのフィールドリストには表示されません。 計算列やメジャーは、パースペクティブに含まれていてもいなくても、除外されているオブジェクト データから計算可能です。  
  
 このレッスンの目的は、パースペクティブの作成方法について理解し、表形式モデルの作成ツールに慣れることです。 後でこのモデルにテーブルを追加する場合は、追加のパースペクティブを作成して、モデルに対する異なるビューポイント (Inventory や Sales Force など) を定義できます。  
  
 詳細については、「[パースペクティブ (SSAS テーブル)](tabular-models/perspectives-ssas-tabular.md)」を参照してください。  
  
 このレッスンの推定所要時間: **5 分**  
  
## <a name="prerequisites"></a>前提条件  
 このトピックは、表形式モデルのチュートリアルの一部であり、順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン「 [レッスン 8: 主要業績評価指標の作成](lesson-7-create-key-performance-indicators.md)」を完了している必要があります。  
  
## <a name="create-perspectives"></a>パースペクティブを作成する  
  
#### <a name="to-create-an-internet-sales-perspective"></a>Internet Sales パースペクティブを作成するには  
  
1.  モデルデザイナーで、[**モデル**] メニューをクリックし、[**パースペクティブ**] をクリックします。  
  
2.  
  **[パースペクティブ]** ダイアログ ボックスで、**[新しいパースペクティブ]** をクリックします。  
  
3.  パースペクティブの名前を変更するには、[**新しいパースペクティブ 1** ] 列見出しをダブル`Internet Sales`クリックし、「」と入力します。  
  
4.  [**フィールド**] で、 **Date**、 **Geography**、 **Product**、 **product Category**、 **product サブカテゴリ**、および`Internet Sales`の各テーブルを選択します。  
  
     Customer テーブルおよびそのすべての列をこのパースペクティブから除外したことに注意してください。 後ほど、レッスン 12 で、"Excel で分析" 機能を使用してこのパースペクティブをテストします。 Excel ピボットテーブルのフィールドの一覧には、Customer テーブルを除く各テーブルが含まれます。  
  
5.  選択内容を確認し、 **Customer** テーブルがオフになっていることを確認して、 **[OK]** をクリックします。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルを続行するには、次のレッスン「 [レッスン 10: 階層の作成](lesson-9-create-hierarchies.md)」に進んでください。  
  
  
