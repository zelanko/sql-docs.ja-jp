---
title: 構造データでのドリルスルーの使用 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a693979c-0564-4d6d-b35d-cbbc8f350469
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 68d5d29a4aed7380bd7a53c65d140aac24912392
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62745543"
---
# <a name="using-drillthrough-on-structure-data-basic-data-mining-tutorial"></a>構造データでのドリルスルーの使用 (基本的なデータ マイニング チュートリアル)
  広告キャンペーンの一環として[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 、は34-40 時代 (人口統計) の潜在顧客に郵便を送信します。 マーケティング部門では、5 年以上前に [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] から自転車を購入した顧客にも宣伝リーフレットを送付することにしました。 このレッスンでは、古い型の自転車を購入した顧客を特定し、その連絡先情報を取得します。 この情報は、モデルではなく構造に含まれています。 連絡先情報を取得するには、まず構造に対してドリルスルーを有効にし、ドリルスルーを使用して対象とする顧客の名前と住所を明らかにします。  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a>マイニング モデルのドリルスルーを有効にするには  
  
1.  のデータマイニングデザイナーの [**マイニングモデル**] タブで、 **TM_Decision_Tree**モデルを右クリックし、[プロパティ] を選択します。 **Properties** [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]  
  
2.  [プロパティ] ウィンドウで **[AllowDrillthrough]** をクリックし、 **[True]** を選択します。  
  
3.  [マイニング モデル] タブでモデルを右クリックし、 **[モデルの処理]** をクリックします。  
  
 詳細については、「[データマイニング &#40;のドリルスルークエリ](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)」を参照してください&#41;  
  
### <a name="to-view-drillthrough-data-from-a-mining-model"></a>マイニング モデルからのドリルスルー データを表示するには  
  
1.  データ マイニング デザイナーで、 **[マイニング モデル ビューアー]** タブをクリックします。  
  
2.  [**マイニングモデル**] ボックスの一覧から**TM_Decision_Tree**モデルを選択します。  
  
3.  [**背景**値をに`1`変更します。 これにより、自転車を購入した顧客に関するモデルの部分のみが表示されます。  
  
4.  **[ビューアー]** ボックスの一覧の [Microsoft ツリー ビューアー] をクリックします。 これにより、ビューアーが強制的に新しいフィルター条件で更新されます。 次に、 **Age >= 34 および <41**ノードを見つけ、ノードを右クリックします。  
  
5.  **[ドリルスルー]** をクリックし、 **[モデルおよび構造列]** をクリックして **[ドリルスルー]** ウィンドウを開きます。  
  
6.  **[Structure.Date First Purchase]** 列までスクロールして、古い型の自転車の購入日を表示します。  
  
7.  データをクリップボードにコピーするには、テーブル内の任意の行を右クリックして **[すべてコピー]** をクリックします。  
  
 これで、「基本的なデータ マイニング チュートリアル」は終了です。 データ マイニング ツールの操作に慣れたら、「中級者向けデータ マイニング チュートリアル」も実行することをお勧めします。「中級者向けデータ マイニング チュートリアル」では、予測、マーケット バスケット分析、シーケンス クラスターの各モデルを作成する方法について説明しています。  
  
## <a name="previous-task-in-lesson"></a>このレッスンの前の作業  
 [予測の作成 &#40;基本的なデータ マイニング チュートリアル&#41;](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [予測クエリ ビルダーを使用した予測クエリの作成](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
