---
title: 作成し、Analysis Services 表形式モデルで Kpi の管理 |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1ae17e727367b702967ec879ed8469973ab3b812
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207735"
---
# <a name="create-and-manage-kpis"></a>作成して、Kpi の管理 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  この記事では、作成、編集、または表形式モデルで KPI (主要業績評価指標) を削除する方法について説明します。 KPI を作成するには、KPI のベース値に評価されるメジャーを選択します。 次に、[主要業績評価指標] ダイアログ ボックスで、評価結果が対象の値になる 2 番目のメジャーまたは絶対値を選択します。 ベース メジャーと対象のメジャーの間のパフォーマンスを測定する、状態のしきい値を定義します。  
  
## <a name="tasks"></a>処理手順  
  
> [!IMPORTANT]  
>  KPI を作成する前に、値を評価するベース メジャーを作成する必要があります。 次に、ベース メジャーを KPI に拡張します。 メジャーを作成する方法が、別のトピックで説明されている[の作成と管理のメジャー](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md)します。 KPI には対象の値も必要です。 この値には事前定義された別のメジャーまたは絶対値を使用できます。 ベース メジャーを KPI に拡張すると、[主要業績評価指標] ダイアログ ボックスで対象の値を選択し、状態のしきい値を定義できます。  
  
###  <a name="bkmk_create_KPI"></a> KPI を作成するには  
  
1.  メジャー グリッドで、ベース メジャー (値) となるメジャーを右クリックし、 **[KPI の作成]** をクリックします。  
  
2.  **[主要業績評価指標]** ダイアログ ボックスの **[ターゲット値の定義]** で、次のいずれかを選択します。  
  
     **[メジャー]** を選択し、リスト ボックスから対象のメジャーを選択します。  
  
     **[絶対値]** を選択し、数値を入力します。  
  
3.  **[状態のしきい値の定義]** で、低いしきい値および高いしきい値をクリックしてスライドします。  
  
4.  **[アイコンのスタイルの選択]** で画像の種類をクリックします。  
  
5.  **[説明]** をクリックして KPI、値、状態、および対象の説明を入力します。  
  
> [!TIP]  
>  Excel で分析機能を使用して、KPI をテストできます。 詳細については、次を参照してください。 [Excel で分析](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)します。  
  
###  <a name="bkmk_edit_KPI"></a> KPI を編集するには  
  
-   メジャー グリッドで、KPI のベース メジャー (値) となるメジャーを右クリックし、 **[KPI 設定の編集]** をクリックします。  
  
###  <a name="bkmk_delete"></a> KPI とベース メジャーを削除するには  
  
-   メジャー グリッドで、KPI のベース メジャー (値) となるメジャーを右クリックし、 **[削除]** をクリックします。  
  
###  <a name="bkmk_delete_KPI"></a> ベース メジャーは削除せずに KPI を削除するには  
  
-   メジャー グリッドで、KPI のベース メジャー (値) となるメジャーを右クリックし、 **[KPI の削除]** をクリックします。  
  
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
  
## <a name="see-also"></a>関連項目  
 [Kpi](../../analysis-services/tabular-models/kpis-ssas-tabular.md)   
 [メジャー](../../analysis-services/tabular-models/measures-ssas-tabular.md)   
 [作成し、managemeasures](../../analysis-services/tabular-models/create-and-manage-measures-ssas-tabular.md)  
  
  
