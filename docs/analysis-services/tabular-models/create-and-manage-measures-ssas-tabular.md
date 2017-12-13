---
title: "作成およびメジャー (SSAS テーブル) の管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edc1a4b2-96d3-4f34-bb70-6cacec79e819
caps.latest.revision: "18"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: e0f4139b090b70ec3f76dc5613abfe3dfabb77cc
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="create-and-manage-measures-ssas-tabular"></a>メジャーを作成および管理する (SSAS テーブル)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]メジャーとは、レポートまたは Excel のピボット テーブル (またはピボット グラフ) で使用中に作成される数式です。 COUNT や SUM などの標準の集計関数に基づいてメジャーを作成することも、DAX を使用して独自の数式を定義することもできます。 このトピックのタスクでは、テーブルのメジャー グリッドを使用してメジャーを作成し管理する方法について説明します。  
  
 このトピックでは、次のタスクについて説明します。  
  
-   [標準の集計式を使用してメジャーを作成するには](#bkmk_create_stand)  
  
-   [カスタム式を使用してメジャーを作成するには](#bkmk_create_custom)  
  
-   [メジャー プロパティを編集するには](#bkmk_edit)  
  
-   [メジャー名を変更するには](#bkmk_rename)  
  
-   [メジャーを削除するには](#bkmk_delete)  
  
## <a name="tasks"></a>処理手順  
 メジャーを作成、管理するには、テーブルのメジャー グリッドを使用します。 テーブルのメジャー グリッドは、モデル デザイナーのデータ ビューのみで表示することができます。 ダイアグラム ビューでは、メジャーの作成もメジャー グリッドの表示もできません。ただし、既存のメジャーであれば、ダイアグラム ビューで表示できます。 あるテーブルのメジャー グリッドを表示するには、 **[テーブル]** メニューをクリックしてから **[メジャー グリッドの表示]**をクリックします。  
  
###  <a name="bkmk_create_stand"></a> 標準の集計式を使用してメジャーを作成するには  
  
-   メジャーを作成する列をクリックし、 **[列]** メニューをクリックしてから **[オート SUM]**をポイントし、集計の種類をクリックします。  
  
     既定名を持つメジャー、そしてその後に数式が列の直下にあるメジャー グリッドの最初のセルに自動的に作成されます。  
  
###  <a name="bkmk_create_custom"></a> カスタム式を使用してメジャーを作成するには  
  
-   メジャー グリッド内のメジャーを作成する列の下で、任意のセルをクリックしてから、数式バーに名前、コロン (:)、等号 (=)、および数式を続けて入力します。 Enter キーを押して数式を確定します。  
  
###  <a name="bkmk_edit"></a> メジャー プロパティを編集するには  
  
-   メジャー グリッド内で、メジャーをクリックしてから **[プロパティ]** ウィンドウで別のプロパティ値を入力するか選択します。  
  
###  <a name="bkmk_rename"></a> メジャー名を変更するには  
  
-   メジャー グリッド内で、メジャーをクリックしてから **[プロパティ]** ウィンドウの **[メジャー名]**ボックスに新しい名前を入力し、Enter キーを押します。  
  
     数式バー内でメジャーの名前を変更することもできます。 メジャー名の後に数式を付け、その後にコロンを付けます。  
  
###  <a name="bkmk_delete"></a> メジャーを削除するには  
  
-   メジャー グリッドで、メジャーを右クリックしてから **[削除]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [メジャー &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/measures-ssas-tabular.md)   
 [KPI &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/kpis-ssas-tabular.md)   
 [計算列 &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/ssas-calculated-columns.md)  
  
  
