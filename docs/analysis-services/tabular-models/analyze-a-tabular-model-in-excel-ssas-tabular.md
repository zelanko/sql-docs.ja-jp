---
title: "Excel (SSAS テーブル) で表形式モデルの分析 |Microsoft ドキュメント"
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
f1_keywords: sql13.asvs.bidtoolset.chooseperspect.f1
ms.assetid: 47fa45fc-60ab-41a1-bde3-5781c8462889
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: fde74281022255a4d14f7bce07d890e20c65e841
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="analyze-a-tabular-model-in-excel-ssas-tabular"></a>Excel でのテーブル モデルの分析 (SSAS テーブル)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]Excel で分析機能で[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]Microsoft Excel を開き、モデル ワークスペース データベースへのデータ ソース接続を作成し、ワークシートにピボット テーブルを追加します。 モデル オブジェクト (テーブル、列、メジャー、階層、および KPI) は、ピボットテーブルのフィールドの一覧にフィールドとして含まれています。  
  
> [!NOTE]  
>  [Excel で分析] 機能を使用するには、レポート デザイナーがインストールされているコンピューターに Microsoft Office 2003 以降が [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]と同じコンピューターにインストールされている必要があります。 Office が同じコンピューターにインストールされていない場合は、別のコンピューターの Excel を使用して、データ ソースとしてモデル ワークスペース データベースに接続できます。 これにより、ピボットテーブルをワークシートに手動で追加することができます。 モデル オブジェクト (テーブル、列、メジャー、および KPI) は、ピボットテーブルのフィールドの一覧にフィールドとして含まれています。  
  
## <a name="tasks"></a>処理手順  
  
#### <a name="to-analyze-a-tabular-model-project-by-using-the-analyze-in-excel-feature"></a>[Excel で分析] 機能を使用してテーブル モデル プロジェクトを分析するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、 **[モデル]** メニューの **[Excel で分析]**をクリックします。  
  
2.  **[資格情報とパースペクティブの選択]** ダイアログ ボックスで、モデル ワークスペース データ ソースに接続するための次のいずれかの資格情報オプションを選択します。  
  
    -   現在のユーザー アカウントを使用するには、 **[現在の Windows ユーザー]**を選択します。  
  
    -   別のユーザー アカウントを使用するには、 **[別の Windows ユーザー]**を選択します。  
  
         通常、このユーザー アカウントはロールのメンバーになります。 パスワードは必要ありません。 このアカウントを使用できるのは、ワークスペース データベースに Excel で接続している場合のみです。  
  
    -   セキュリティ ロールを使用するには、 **[ロール]**を選択して、一覧から 1 つ以上のロールを選択します。  
  
         セキュリティ ロールはロール マネージャーを使用して定義する必要があります。 詳細については、「[ロールの作成および管理 (SSAS テーブル)](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md)」を参照してください。  
  
3.  パースペクティブを使用するには、**[パースペクティブ]** ボックスの一覧からパースペクティブを選択します。  
  
     パースペクティブ (既定値以外) は [パースペクティブ] ダイアログ ボックスを使用して定義する必要があります。 詳細については、「[パースペクティブの作成と管理 (SSAS テーブル)](../../analysis-services/tabular-models/create-and-manage-perspectives-ssas-tabular.md)」を参照してください。  
  
> [!NOTE]  
>  Excel のピボットテーブルのフィールドの一覧は、モデル デザイナーでモデル プロジェクトに変更を加えても自動的に更新されません。 ピボットテーブルのフィールドの一覧を更新するには、Excel の **[オプション]** リボンで **[更新]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [Excel で分析 (SSAS テーブル)](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)  
  
  
