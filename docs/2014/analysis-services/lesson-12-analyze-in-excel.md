---
title: 'レッスン 13: Excel で分析する |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: ce717071-193b-4c99-9654-c7a613e16327
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6a1564a2b190703e011624162ad4bc25fd5de794
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66079189"
---
# <a name="lesson-13-analyze-in-excel"></a>レッスン 13:[Excel で分析]
  このレッスンでは、 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] で "Excel で分析" 機能を使用して Microsoft Excel を開き、モデル ワークスペースへのデータ ソース接続を自動的に作成して、ワークシートにピボットテーブルを自動的に追加します。 Analyze in Excel 機能は､モデルをデプロイする前にモデル デザインの有効性を迅速かつ簡単にテストする手段を提供することを意図しています｡ このレッスンでは、データの分析は行いません。 このレッスンの目的はモデル作成者が､モデル デザインのテストに利用できるツールを慣れてもらうことにあります｡ モデル作成者向けの "Excel で分析" 機能を使用する場合とは異なり、エンド ユーザーは Excel や [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] などのクライアント レポート アプリケーションを使用して、配置済みのモデル データへの接続と参照を行います。  
  
 このレッスンを完了するには、 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]と同じコンピューター上に Excel がインストールされている必要があります。 詳細については、「[Excel で分析 (SSAS テーブル)](tabular-models/analyze-in-excel-ssas-tabular.md)」を参照してください。  
  
 このレッスンの推定所要時間: **20 分**  
  
## <a name="prerequisites"></a>前提条件  
 このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン「 [レッスン 11: パーティションの作成](lesson-10-create-partitions.md)」を完了している必要があります。  
  
## <a name="browse-using-the-default-and-internet-sales-perspectives"></a>Default および Internet Sales パースペクティブを使用して参照します｡  
 ここでは、すべてのモデル オブジェクトを含む既定のパースペクティブと「レッスン 8: パースペクティブの作成」で作成した Internet Sales パースペクティブの両方を使用してモデルを参照します。 Internet Sales パースペクティブでは、Customer テーブル オブジェクトが除外されます。  
  
#### <a name="to-browse-by-using-the-default-perspective"></a>Default パースペクティブを使って参照する  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、 **[モデル]** メニューの **[Excel で分析]** をクリックします。  
  
2.  **[Analyze in Excel]** ダイアログ ボックスで **[OK]** をクリックします｡  
  
     新しいノートブックで Excel が開きます｡ 現在のユーザー アカウントを使用してデータ ソース接続が作成され、既定のパースペクティブを使用して表示可能なフィールドが定義されます。 ピボットテーブルがワークシートに自動的に追加されます。  
  
3.  Excel の [**ピボットテーブルのフィールドリスト**] に、 **Date**および**internet sales**メジャーが表示され、 **Customer**、 **date**、 **Geography**、 **product**、 **product Category**、 **product サブカテゴリ**、および**internet sales**の各テーブルにそれぞれの列が表示されます。  
  
4.  ブックを保存せずに Excel を閉じます。  
  
#### <a name="to-browse-by-using-the-internet-sales-perspective"></a>Internet Sales パースペクティブを使って参照する  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、 **[モデル]** メニューの **[Excel で分析]** をクリックします。  
  
2.  **[Excel で分析]** ダイアログ ボックスの **[現在の Windows ユーザー]** を選択したままにして、 **[パースペクティブ]** ドロップダウン リストで **[Internet Sales]** を選択し、 **[OK]** をクリックします。 Excel が開きます。  
  
3.  Excel の **[ピボットテーブルのフィールドリスト]** で、フィールドリストから Customer テーブルが除外されます。  
  
## <a name="browse-using-roles"></a>ロールを使用した参照  
 ロールはテーブル モデルに欠かせない要素です。 ユーザーがメンバーとして追加されているロールが少なくとも 1 つなければ、ユーザーはモデルを使用してデータにアクセスし、分析することができません。 "Excel で分析" 機能を利用して、定義したロールをテストすることができます。  
  
#### <a name="to-browse-by-using-the-internet-sales-manager-user-role"></a>Internet Sales Manager ユーザー ロールを使用して参照するには  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、 **[モデル]** メニューの **[Excel で分析]** をクリックします。  
  
2.  **[Excel で分析]** ダイアログ ボックスの **[モデルへの接続に使用するユーザー名またはロールの指定]** で、 **[ロール]** を選択します。次にドロップダウン リストで **[Internet Sales Manager]** を選択し、 **[OK]** をクリックします。  
  
     新しいノートブックで Excel が開きます｡ ピボット テーブルが自動的に作成されます。 [ピボット テーブル フィールド リスト] には、新しいモデルで使用できるすべてのデータ フィールドが表示されます。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルを続行するには、次のレッスン「 [レッスン 14: 配置](lesson-13-deploy.md)」に進んでください。  
  
  
