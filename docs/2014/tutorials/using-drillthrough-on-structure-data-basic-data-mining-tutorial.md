---
title: 構造データ (基本的なデータ マイニング チュートリアル) でのドリルスルーの使用 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a693979c-0564-4d6d-b35d-cbbc8f350469
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 71a8fa3ac449c8d9427ea138206fbd0c1ea8f1ef
ms.sourcegitcommit: 8c040e5b4e8c7d37ca295679410770a1af4d2e1f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2018
ms.locfileid: "36312460"
---
# <a name="using-drillthrough-on-structure-data-basic-data-mining-tutorial"></a>構造データでのドリルスルーの使用 (基本的なデータ マイニング チュートリアル)
  広告キャンペーンの一部として[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]は宣伝リーフレットを送付する潜在的な顧客 34 ~ 40 歳の人口統計。 マーケティング部門は、メーラーをから自転車を購入した顧客に送信するも宣伝をしました[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]5 年以上前です。 このレッスンでは、古い型の自転車を購入した顧客を特定し、その連絡先情報を取得します。 この情報は、モデルではなく構造に含まれています。 連絡先情報を取得するには、まず構造に対してドリルスルーを有効にし、ドリルスルーを使用して対象とする顧客の名前と住所を明らかにします。  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a>マイニング モデルのドリルスルーを有効にするには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]の**マイニング モデル**] タブのデータ マイニング デザイナーを右クリックし、 **TM_Decision_Tree**モデル、および選択**プロパティ**です。  
  
2.  [プロパティ] ウィンドウで **[AllowDrillthrough]** をクリックし、 **[True]** を選択します。  
  
3.  マイニング モデル タブで、モデルを右クリックして**プロセス モデル**です。  
  
 詳細については、次を参照してください[ドリルスルー クエリ&#40;データ マイニング。&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)  
  
### <a name="to-view-drillthrough-data-from-a-mining-model"></a>マイニング モデルからのドリルスルー データを表示するには  
  
1.  データ マイニング デザイナーで、 **[マイニング モデル ビューアー]** タブをクリックします。  
  
2.  選択、 **TM_Decision_Tree**からモデル、**マイニング モデルの** ボックスの一覧です。  
  
3.  変更、**背景**値を`1`です。 これにより、自転車を購入した顧客に関するモデルの部分のみが表示されます。  
  
4.  **[ビューアー]** ボックスの一覧の [Microsoft ツリー ビューアー] をクリックします。 これにより、ビューアーが強制的に新しいフィルター条件で更新されます。 検索、 **Age > = 34 と < 41**ノードと、ノードを右クリックします。  
  
5.  **[ドリルスルー]** をクリックし、 **[モデルおよび構造列]** をクリックして **[ドリルスルー]** ウィンドウを開きます。  
  
6.  **[Structure.Date First Purchase]** 列までスクロールして、古い型の自転車の購入日を表示します。  
  
7.  データをクリップボードにコピーするには、テーブル内の任意の行を右クリックして **[すべてコピー]** をクリックします。  
  
 これで、「基本的なデータ マイニング チュートリアル」は終了です。 データ マイニング ツールの操作に慣れたら、「中級者向けデータ マイニング チュートリアル」も実行することをお勧めします。「中級者向けデータ マイニング チュートリアル」では、予測、マーケット バスケット分析、シーケンス クラスターの各モデルを作成する方法について説明しています。  
  
## <a name="previous-task-in-lesson"></a>このレッスンの前の作業  
 [予測の作成&#40;基本的なデータ マイニングのチュートリアル&#41;](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [予測クエリ ビルダーを使用した予測クエリの作成](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  