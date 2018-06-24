---
title: 'レッスン 8: 主要業績評価指標の作成 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a6c8ac2b-64ba-456f-b418-7bf0afe145d1
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.openlocfilehash: fd135a37a4fe2721ca6aaa70d25e869b9a83733e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073599"
---
# <a name="lesson-8-create-key-performance-indicators"></a>レッスン 8: 主要業績評価指標の作成
  このレッスンでは、主要業績評価指標 (KPI) を作成します。 KPI は、値のパフォーマンスを測定するために使用されます。パフォーマンスは、 *"ベース"* メジャーと *"ターゲット"* 値の対比によって定義されます (メジャーまたは絶対値によっても定義できます)。 KPI を使用すると、ビジネス プロフェッショナルがレポート クライアント アプリケーションを通じて、ビジネスの成功度や傾向をすばやく簡単に把握できるようになります。 詳細については、[「KPI (SSAS テーブル)」](tabular-models/kpis-ssas-tabular.md) を参照してください。  
  
 このレッスンの推定所要時間: **15 分**  
  
## <a name="prerequisites"></a>前提条件  
 このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン [「レッスン 7: メジャーの作成」](lesson-6-create-measures.md) を完了している必要があります。  
  
## <a name="create-key-performance-indicators"></a>主要業績評価指標の作成  
  
#### <a name="to-create-an-internet-current-quarter-sales-performance-kpi"></a>Internet Current Quarter Sales Performance KPI を作成するには  
  
1.  モデル デザイナーで、**[Internet Sales]** テーブル (タブ) をクリックします。  
  
2.  メジャー グリッドで、空のセルをクリックします。  
  
3.  テーブルの上にある数式バーに、以下の数式を入力します。  
  
     `Internet Current Quarter Sales Performance :=IFERROR([Internet Current Quarter Sales]/[Internet Previous Quarter Sales Proportion to QTD],BLANK())`  
  
     数式の入力が終了したら、Enter キーを押します。  
  
     このメジャーは、KPI のベース メジャーとして機能します。  
  
4.  メジャー グリッドで、 **Internet Current Quarter Sales Performance** メジャーを右クリックし、**[KPI の作成]** をクリックします。  
  
     **[主要業績評価指標]** ダイアログ ボックスが開きます。  
  
5.  **[主要業績評価指標]** ダイアログ ボックスの **[ターゲット値の定義]** で、**[絶対値]** オプションを選択します。  
  
6.  **絶対値**フィールドに「 `1.1`、ENTER キーを押します。  
  
7.  **ステータスのしきい値の定義**、(低) の左のスライダー フィールドに「 `1`、し、右 (高) スライダー フィールドに「`1.07`です。  
  
8.  **[アイコンのスタイルの選択]** で、ひし形 (赤)、三角形 (黄)、円 (緑) のアイコンの種類を選択します。  
  
    > [!TIP]  
    >  使用可能なアイコン スタイルの下には **[説明]** という展開可能フィールドがあります。 各種の KPI 要素に対する説明を入力することで、それらをクライアント アプリケーションで識別しやすくすることができます。  
  
9. **[OK]** をクリックして KPI の作成を完了します。  
  
     メジャー グリッドで、 **Internet Current Quarter Sales Performance** メジャーの横にアイコンが表示されます。 このアイコンは、そのメジャーが KPI のベース値として機能することを示します。  
  
#### <a name="to-create-an-internet-current-quarter-margin-performance-kpi"></a>Internet Current Quarter Margin Performance KPI を作成するには  
  
1.  **Internet Sales** テーブルのメジャー グリッドで、空のセルをクリックします。  
  
2.  テーブルの上にある数式バーに、以下の数式を入力します。  
  
     `Internet Current Quarter Margin Performance :=IF([Internet Previous Quarter Margin Proportion to QTD]<>0,([Internet Current Quarter Margin]-[Internet Previous Quarter Margin Proportion to QTD])/[Internet Previous Quarter Margin Proportion to QTD],BLANK())`  
  
     数式の入力が終了したら、Enter キーを押します。  
  
3.  メジャー グリッドで、 **Internet Current Quarter Margin Performance** メジャーを右クリックし、**[KPI の作成]** をクリックします。  
  
4.  **[主要業績評価指標]** ダイアログ ボックスの **[ターゲット値の定義]** で、**[絶対値]** オプションを選択します。  
  
5.  **絶対値**フィールドに「`1.25`です。  
  
6.  **[ステータスのしきい値の定義]** で、左 (下) のスライダー フィールドをスライドして「 **0.8**」と表示させ、右 (上) のスライダー フィールドをスライドして「 **1.03**」と表示させます。  
  
7.  **[アイコンのスタイルの選択]** で、ひし形 (赤)、三角形 (黄)、円 (緑) のアイコンの種類を選択し、**[OK]** をクリックします。  
  
## <a name="next-step"></a>次の手順  
 このチュートリアルを続行するには、次のレッスン [「レッスン 9: パースペクティブの作成」](lesson-8-create-perspectives.md) に進んでください。  
  
  