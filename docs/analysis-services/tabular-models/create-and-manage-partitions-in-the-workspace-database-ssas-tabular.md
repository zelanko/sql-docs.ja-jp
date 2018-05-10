---
title: 作成し、ワークスペース データベースでパーティションを管理する |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7ba29f6beba076049a097ad4b0d3057d75f7846b
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2018
---
# <a name="create-and-manage-partitions-in-the-workspace-database"></a>ワークスペース データベースでのパーティション作成し、管理 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  パーティションは、テーブルを論理的な部分に分割します。 その後、各パーティションは、個別に、または他のパーティションと並列に処理 (更新) することができます。 パーティションによって、大規模なデータベースのスケーラビリティと管理性を向上させることができます。 既定では、各テーブルに 1 つのパーティションがあり、すべての列がこのパーティションに含まれます。 このトピックのタスクを作成しを使用して、モデル ワークスペース データベースでパーティションを管理する方法について説明、 **Partition Manager**  ダイアログ ボックス[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]  
  
 別の Analysis Services インスタンスにモデルが配置された後、データベース管理者は、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して (配置済みの) モデルでパーティションを作成し管理できます。 詳細については、次を参照してください。[作成および表形式モデル パーティションの管理](../../analysis-services/tabular-models/create-and-manage-tabular-model-partitions-ssas-tabular.md)です。  
  
> [!NOTE]  
>  [パーティション マネージャー] ダイアログ ボックスを使用して、モデル ワークスペース データベースのパーティションを結合することはできません。 パーティションが結合できるのは、配置されたモデルで [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用した場合のみです。  
  
## <a name="tasks"></a>処理手順  
 パーティションの作成と管理には、 **[パーティション マネージャー]** ダイアログ ボックスを使用します。 **[パーティション マネージャー]** ダイアログ ボックスを表示するには、 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]の **[テーブル]** メニューをクリックし、 **[パーティション]** をクリックします。  
  
###  <a name="bkmk_create_new"></a> 新しいパーティションを作成するには  
  
1.  モデル デザイナーで、パーティションを定義するテーブルを選択します。  
  
2.  **[テーブル]** メニューをクリックし、 **[パーティション]** をクリックします。  
  
3.  **[パーティション マネージャー]** の **[テーブル]** ボックスの一覧で、パーティション分割するテーブルを確認または選択し、 **[新規作成]** をクリックします。  
  
4.  **[パーティション名]** にパーティションの名前を入力します。 既定では、既定のパーティション名に番号が付き、新しいパーティションを作成するたびにその番号が増加します。  
  
5.  テーブル プレビュー モードを使用するか、クエリ エディター モードを使用して作成した SQL クエリを使用すると、パーティションに含める行と列を選択できます。  
  
     テーブル プレビュー モード (既定) を使用するには、プレビュー ウィンドウの右上隅にある **[テーブル プレビュー]** ボタンをクリックします。 列名の横のチェック ボックスをオンにして、パーティションに含める列を選択します。 行をフィルター選択するには、セル値を右クリックし、 **[選択したセル値でフィルター]** をクリックします。  
  
     SQL ステートメントを使用するには、プレビュー ウィンドウの右上隅にある **[クエリ エディター]** ボタンをクリックしてから、クエリ ウィンドウに SQL クエリ ステートメントを入力するか貼り付けます。 ステートメントを検証するには、 **[検証]** をクリックします。 クエリ デザイナーを使用するには、 **[デザイン]** をクリックします。  
  
###  <a name="bkmk_copy"></a> パーティションをコピーするには  
  
1.  **[パーティション マネージャー]** の **[テーブル]** ボックスの一覧で、コピーするパーティションが含まれているテーブルを確認または選択します。  
  
2.  **[パーティション]** リストでコピーするパーティションを選択し、 **[コピー]** をクリックします。  
  
3.  **[パーティション名]** にパーティションの新しい名前を入力します。  
  
###  <a name="bkmk_delete"></a> パーティションを削除するには  
  
1.  **[パーティション マネージャー]** の **[テーブル]** ボックスの一覧で、削除するパーティションが含まれているテーブルを確認または選択します。  
  
2.  **[パーティション]** リストで削除するパーティションを選択し、 **[削除]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [パーティション](../../analysis-services/tabular-models/partitions-ssas-tabular.md)   
 [ワークスペース データベースでパーティションの処理](../../analysis-services/tabular-models/process-partitions-in-the-workspace-databse-ssas-tabular.md)  
  
  
