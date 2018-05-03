---
title: Excel でテーブル モデルの分析 |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/21/2018
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.asvs.bidtoolset.chooseperspect.f1
ms.assetid: 47fa45fc-60ab-41a1-bde3-5781c8462889
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3ca204d3656f6f527992c8b9205fb593af53e623
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="analyze-a-tabular-model-in-excel"></a>Excel でテーブル モデルを分析します。  
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] の [Excel で分析] 機能によって Microsoft Excel が開き、モデル ワークスペース データベースへのデータ ソース接続が作成され、ピボットテーブルがワークシートに追加されます。 モデル オブジェクト (テーブル、列、メジャー、階層、および KPI) は、ピボットテーブルのフィールドの一覧にフィールドとして含まれています。  
  
> [!NOTE]  
>  [Excel で分析] 機能を使用するには、レポート デザイナーがインストールされているコンピューターに Microsoft Office 2003 以降が [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]と同じコンピューターにインストールされている必要があります。 Office が同じコンピューターにインストールされていない場合は、別のコンピューターの Excel を使用して、データ ソースとしてモデル ワークスペース データベースに接続できます。 これにより、ピボットテーブルをワークシートに手動で追加することができます。 モデル オブジェクト (テーブル、列、メジャー、および KPI) は、ピボットテーブルのフィールドの一覧にフィールドとして含まれています。  
  
## <a name="tasks"></a>処理手順  
  
#### <a name="to-analyze-a-tabular-model-project-by-using-the-analyze-in-excel-feature"></a>[Excel で分析] 機能を使用してテーブル モデル プロジェクトを分析するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で、 **[モデル]** メニューの **[Excel で分析]** をクリックします。  
  
2.  **[資格情報とパースペクティブの選択]** ダイアログ ボックスで、モデル ワークスペース データ ソースに接続するための次のいずれかの資格情報オプションを選択します。  
  
    -   現在のユーザー アカウントを使用するには、 **[現在の Windows ユーザー]** を選択します。  
  
    -   別のユーザー アカウントを使用するには、 **[別の Windows ユーザー]** を選択します。  
  
         通常、このユーザー アカウントはロールのメンバーになります。 パスワードは必要ありません。 このアカウントを使用できるのは、ワークスペース データベースに Excel で接続している場合のみです。  
  
    -   セキュリティ ロールを使用するには、 **[ロール]** を選択して、一覧から 1 つ以上のロールを選択します。  
  
         セキュリティ ロールはロール マネージャーを使用して定義する必要があります。 詳細については、次を参照してください。[作成と管理の役割](../../analysis-services/tabular-models/create-and-manage-roles-ssas-tabular.md)です。  
  
3.  パースペクティブを使用するには、**[パースペクティブ]** ボックスの一覧からパースペクティブを選択します。  
  
     パースペクティブ (既定値以外) は [パースペクティブ] ダイアログ ボックスを使用して定義する必要があります。 詳細については、次を参照してください。[管理パースペクティブの作成および](../../analysis-services/tabular-models/create-and-manage-perspectives-ssas-tabular.md)です。  
  
> [!NOTE]  
>  Excel のピボットテーブルのフィールドの一覧は、モデル デザイナーでモデル プロジェクトに変更を加えても自動的に更新されません。 ピボットテーブルのフィールドの一覧を更新するには、Excel の **[オプション]** リボンで **[更新]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [Excel で分析します。](../../analysis-services/tabular-models/analyze-in-excel-ssas-tabular.md)  
  
  
