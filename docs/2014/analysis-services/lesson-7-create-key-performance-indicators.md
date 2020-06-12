---
title: 'レッスン 8: 主要業績評価指標を作成する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a6c8ac2b-64ba-456f-b418-7bf0afe145d1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 123393c061d151240949f41e59e5d14b19056c52
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84542321"
---
# <a name="lesson-8-create-key-performance-indicators"></a>レッスン 8: 主要業績評価指標を作成する
  このレッスンでは、主要業績評価指標 (KPI) を作成します。 KPI は、値のパフォーマンスを測定するために使用されます。パフォーマンスは、 *"ベース"* メジャーと *"ターゲット"* 値の対比によって定義されます (メジャーまたは絶対値によっても定義できます)。 レポート用のクライアント アプリケーションでは､KPI はビジネスのプロが事業の成功の摘要を理解したり､傾向を把握したりする容易で迅速な手段になります｡ 詳細については、[「KPI (SSAS テーブル)」](tabular-models/kpis-ssas-tabular.md) を参照してください。  
  
 このレッスンの推定所要時間: **15 分**  
  
## <a name="prerequisites"></a>前提条件  
 このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン [「レッスン 7: メジャーの作成」](lesson-6-create-measures.md)を完了している必要があります。  
  
## <a name="create-key-performance-indicators"></a>主要業績評価指標を作成する  
  
#### <a name="to-create-an-internet-current-quarter-sales-performance-kpi"></a>Internet Current Quarter Sales Performance KPI を作成するには  
  
1.  モデル デザイナーで、[ **Internet Sales** ] テーブル (タブ) をクリックします。  
  
2.  メジャー グリッドで、空のセルをクリックします。  
  
3.  テーブルの上の数式バーに次の式を入力します｡  
  
     `Internet Current Quarter Sales Performance :=IFERROR([Internet Current Quarter Sales]/[Internet Previous Quarter Sales Proportion to QTD],BLANK())`  
  
     数式の入力が終了したら、Enter キーを押します。  
  
     このメジャーは、KPI のベース メジャーとして機能します。  
  
4.  メジャー グリッドで、 **Internet Current Quarter Sales Performance** メジャーを右クリックし、[ **KPI の作成**] をクリックします。  
  
     [ **主要業績評価指標** ] ダイアログ ボックスが開きます。  
  
5.  [ **主要業績評価指標** ] ダイアログ ボックスの [ **ターゲット値の定義**] で、[ **絶対値** ] オプションを選択します。  
  
6.  [**絶対値**] フィールドに「」と入力し、enter `1.1` キーを押します。  
  
7.  [**状態のしきい値の定義**] で、左 (下) のスライダーフィールドに「」と入力し、 `1` 右 (高) のスライダーフィールドに「」と入力し `1.07` ます。  
  
8.  [ **アイコンのスタイルの選択**] で、ひし形 (赤)、三角形 (黄)、円 (緑) のアイコンの種類を選択します。  
  
    > [!TIP]  
    >  使用可能なアイコン スタイルの下には [ **説明** ] という展開可能フィールドがあります。 各種の KPI 要素に対する説明を入力することで、それらをクライアント アプリケーションで識別しやすくすることができます。  
  
9. [ **OK** ] をクリックして KPI の作成を完了します。  
  
     メジャー グリッドで、 **Internet Current Quarter Sales Performance** メジャーの横にアイコンが表示されます。 このアイコンは、そのメジャーが KPI のベース値として機能することを示します。  
  
#### <a name="to-create-an-internet-current-quarter-margin-performance-kpi"></a>Internet Current Quarter Margin Performance KPI を作成するには  
  
1.  **Internet Sales** テーブルのメジャー グリッドで、空のセルをクリックします。  
  
2.  テーブルの上の数式バーに次の式を入力します｡  
  
     `Internet Current Quarter Margin Performance :=IF([Internet Previous Quarter Margin Proportion to QTD]<>0,([Internet Current Quarter Margin]-[Internet Previous Quarter Margin Proportion to QTD])/[Internet Previous Quarter Margin Proportion to QTD],BLANK())`  
  
     数式の入力が終了したら、Enter キーを押します。  
  
3.  メジャー グリッドで、 **Internet Current Quarter Margin Performance** メジャーを右クリックし、[ **KPI の作成**] をクリックします。  
  
4.  [ **主要業績評価指標** ] ダイアログ ボックスの [ **ターゲット値の定義**] で、[ **絶対値** ] オプションを選択します。  
  
5.  [**絶対値**] フィールドに「」と入力 `1.25` します。  
  
6.  [ **ステータスのしきい値の定義**] で、左 (下) のスライダー フィールドをスライドして「 **0.8**」と表示させ、右 (上) のスライダー フィールドをスライドして「 **1.03**」と表示させます。  
  
7.  **[Select Icon Style]** で､アイコン タイプとして菱形 (赤)､三角形 (黄色)､円 (緑) を選択し､**[OK]** をクリックします｡  
  
## <a name="next-step"></a>次の手順  
 このチュートリアルを続行するには、次のレッスン [「レッスン 9: パースペクティブの作成」](lesson-8-create-perspectives.md)に進んでください。  
  
  
