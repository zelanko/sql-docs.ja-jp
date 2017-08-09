---
title: "Reporting Services で Kpi を操作する |Microsoft ドキュメント"
ms.date: 07/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a28cf500-6d47-4268-a248-04837e7a09eb
caps.latest.revision: 13
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: dcf26be9dc2e502b2d01f5d05bcb005fd7938017
ms.openlocfilehash: f8057d09bb9118ef5575645f3fab9ba7a1fede94
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---

# <a name="working-with-kpis-in-reporting-services"></a>Reporting Services で KPI を使用する

[!INCLUDE[ssrs-appliesto](../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016-and-later](../includes/ssrs-appliesto-2016-and-later.md)] [!INCLUDE[ssrs-appliesto-pbirsi](../includes/ssrs-appliesto-pbirs.md)]

主要業績評価指標 (KPI) は、目標に対する達成度の伝達を視覚化したものです。  主要業績評価指標は、チーム、マネージャー、およびビジネスにとって、測定可能な目標に対する進捗度をすばやく評価するうえで重要です。   
  
SQL Server 2016 Reporting Services で KPI を使用することで、以下の質問に対する回答を簡単に視覚化できます。  
  
-   どの目標を達成していて、どの目標を達成していないか。  
  
-   どの程度進んでいるか、または遅れているか。  
  
-   最低限完了したことは何か。  
  
## <a name="creating-a-dataset"></a>データセットの作成  
KPI は、共有データセットの最初の行のデータのみを使用します。 使用したいデータがその最初の行にあることを確認します。 共有データセットを作成するには、レポート ビルダーまたは SQL Server Data Tools のいずれかを使用することができます。  
  
> **注**: Dataset は、KPI と同じフォルダーに配置する必要はありません。  
  
## <a name="placement-of-kpis"></a>KPI の配置  
  
KPI は、レポート サーバーの任意のフォルダーに作成できます。  KPI を作成する前に、それを配置する適切な場所について検討する必要があります。 他のレポートおよびそれに関する KPI に関係があり、ユーザーが参照できるフォルダーに配置する必要があります。  
  
## <a name="adding-a-kpi"></a>KPI を追加する  
  
KPI の場所を決定したら、そのフォルダーに移動して、トップ メニューから [ **新規** > **KPI** ] を選択します。  
  
![rsCreateKPI1](../reporting-services/media/rscreatekpi1.png)  
  
これにより、[ **新しい KPI** ] 画面が表示されます。  
  
![rsCreateKPI2](../reporting-services/media/rscreatekpi2.png)  
  
静的な値を割り当てるか、共有データセットのデータを使用できます。 新しい KPI を作成する場合、ランダムなデータセットを手動で入力します。  
  
|フィールド|Description|  
|---|---|  
|値の表示形式|  表示される値の形式を変更するために使用します。|   
|値|表示する KPI の値。|  
|[目標]|数値との比較として使用され、比率の差として表示されます。|  
|[状態]|KPI タイルの色を決定するために使用される数値。 有効な値は 1 (緑)、0 (黄色) および-1 (赤です)。|  
|トレンド セット|グラフを視覚化するために使用されるコンマ区切りの数値。 これは、傾向を表す値を含むデータセットの列にも設定できます。|  
  
> **警告**: 設計時には [ **ステータス** ] フィールドに文字値を使用できますが、データセットを更新する場合、数値を使用する必要があります。 数値ではなく文字値を含むデータセットを更新すると、サーバー上の KPI が破損する可能性があります。  
  
> **注**: [ **値**]、[ **目標** ]、[ **状態** ] の各フィールドの値は、データセットの結果の最初の行からのみ選択できます。 ただし、[ **トレンド セット** ] フィールドでは、傾向を反映する列を選択できます。  
  
共有データセットのデータを使用するには、次の操作を実行します。  
  
1.  [フィールド] ドロップダウン ボックスを [ **手動設定**] または [ **未設定**] から [ **データセット フィールド**] に変更します。  
  
    ![rsCreateKPI3](../reporting-services/media/rscreatekpi3.png)  
  
2.  選択、**省略記号 (...)**データ ボックスにします。 これにより、[ **データセットの選択** ] 画面が表示されます。  
  
    ![rsCreateKPI4](../reporting-services/media/rscreatekpi4.png)  
  
3.  表示するデータを含むデータセットを選択します。  
  
4.  使用するフィールドを選択します。 [ **OK**] を選択します。  
  
    ![rsCreateKPI5](../reporting-services/media/rscreatekpi5.png)  
  
5.  値の形式と一致するように [ **値の表示形式** ] を変更します。 この例では、値は通貨です。  
  
    ![rsCreateKPI6](../reporting-services/media/rscreatekpi6.png)  
  
6.  [ **適用**] を選択します。  
  
    ![rsCreateKPI7](../reporting-services/media/rscreatekpi7.png)  
  
## <a name="removing-a-kpi"></a>KPI を削除する  
  
KPI を削除するには、次の操作を実行します。  
  
1.  選択、**省略記号 (...)**を削除する KPI のです。 [ **管理**] を選択します。  
  
    ![rsRemoveKPI1](../reporting-services/media/rsremovekpi1.png)  
  
2.  [ **削除**] を選択します。 確認ダイアログで [ **削除** ] を再度選択します。  
  
    ![rsRemoveKPI2](../reporting-services/media/rsremovekpi2.png)  
  
## <a name="refreshing-a-kpi"></a>KPI を更新する  
  
KPI を更新するには、共有データセットのキャッシュを構成する必要があります。 更新計画のキャッシュに関する詳細についてを参照してください[共有データセットを操作](../reporting-services/work-with-shared-datasets-web-portal.md)です。  
  
## <a name="next-steps"></a>次の手順
  
[Web ポータル](../reporting-services/web-portal-ssrs-native-mode.md)  
[共有データセットを操作します。](../reporting-services/work-with-shared-datasets-web-portal.md)

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)
