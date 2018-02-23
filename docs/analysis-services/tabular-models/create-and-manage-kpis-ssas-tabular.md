---
title: "作成および管理 Kpi |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/22/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.bidtoolset.kpi.f1
ms.assetid: c96026c2-4394-4c3c-986b-4c95a4421900
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: b16307f79552529c2afc0c1d298c68a85ff1f2a1
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="create-and-manage-kpis"></a>作成および管理の Kpi 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
この記事では、作成、編集、または表形式モデルで KPI (主要業績評価指標) を削除する方法について説明します。 KPI を作成するには、評価結果が KPI のベース値になるメジャーを選択します。 次に、[主要業績評価指標] ダイアログ ボックスで、評価結果が対象の値になる 2 番目のメジャーまたは絶対値を選択します。 ベース メジャーと対象のメジャーの間のパフォーマンスを測定する、状態のしきい値を定義します。  
  
## <a name="tasks"></a>処理手順  
  
> [!IMPORTANT]  
>  KPI を作成する前に、値を評価するベース メジャーを作成する必要があります。 次に、ベース メジャーを KPI に拡張します。 メジャーを作成する方法が他のトピックで説明されている[作成と管理メジャー](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md)です。 KPI には対象の値も必要です。 この値には事前定義された別のメジャーまたは絶対値を使用できます。 ベース メジャーを KPI に拡張すると、[主要業績評価指標] ダイアログ ボックスで対象の値を選択し、状態のしきい値を定義できます。  
  
###  <a name="bkmk_create_KPI"></a> KPI を作成するには  
  
1.  メジャー グリッドで、ベース メジャー (値) となるメジャーを右クリックし、 **[KPI の作成]**をクリックします。  
  
2.  **[主要業績評価指標]** ダイアログ ボックスの **[ターゲット値の定義]**で、次のいずれかを選択します。  
  
     **[メジャー]**を選択し、リスト ボックスから対象のメジャーを選択します。  
  
     **[絶対値]**を選択し、数値を入力します。  
  
3.  **[状態のしきい値の定義]**で、低いしきい値および高いしきい値をクリックしてスライドします。  
  
4.  **[アイコンのスタイルの選択]**で画像の種類をクリックします。  
  
5.  **[説明]**をクリックして KPI、値、状態、および対象の説明を入力します。  
  
> [!TIP]  
>  Excel で分析機能を使用して、KPI をテストできます。 詳細については、次を参照してください。 [Excel で分析](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)です。  
  
###  <a name="bkmk_edit_KPI"></a> KPI を編集するには  
  
-   メジャー グリッドで、KPI のベース メジャー (値) となるメジャーを右クリックし、 **[KPI 設定の編集]**をクリックします。  
  
###  <a name="bkmk_delete"></a> KPI とベース メジャーを削除するには  
  
-   メジャー グリッドで、KPI のベース メジャー (値) となるメジャーを右クリックし、 **[削除]**をクリックします。  
  
###  <a name="bkmk_delete_KPI"></a> ベース メジャーは削除せずに KPI を削除するには  
  
-   メジャー グリッドで、KPI のベース メジャー (値) となるメジャーを右クリックし、 **[KPI の削除]**をクリックします。  
  
## <a name="alt-shortcuts"></a>ALT ショートカット  
  
|UI セクション|キー コマンド|  
|----------------|-----------------|  
|KPI ベース メジャー|Alt + B|  
|KPI ステータス|Alt + S|  
|[メジャー]|Alt + M|  
|[絶対値]|Alt + A|  
|[状態のしきい値の定義]|Alt + U|  
|[アイコンのスタイルの選択]|Alt&lt;/localizedText&gt; + &lt;localizedText&gt;I|  
|傾向|Alt + T|  
|[説明]|Alt + D|  
|傾向|Alt + T|  
  
## <a name="see-also"></a>参照  
 [Kpi](../../analysis-services/tabular-models/kpis-ssas-tabular.md)   
 [メジャー](../../analysis-services/tabular-models/measures-ssas-tabular.md)   
 [作成し、managemeasures](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md)  
  
  
