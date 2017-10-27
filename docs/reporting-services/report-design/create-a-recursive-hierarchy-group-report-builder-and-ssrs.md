---
title: "再帰型階層グループ (レポート ビルダーおよび SSRS) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b830ba5-4d64-4348-a2b1-76b9338a1462
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2adde1d53084f92ee16822c5b6d04a886f31fe28
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="create-a-recursive-hierarchy-group-report-builder-and-ssrs"></a>再帰型階層グループの作成 (レポート ビルダーおよび SSRS)
[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のページ分割されたレポートでは、再帰型階層グループは、組織階層内のマネージャーと従業員のリレーションシップを表す上司/部下構造など、複数の階層レベルから成る単一のレポート データセットのデータを編成します。  
  
 テーブル内のデータを再帰型階層グループにまとめるには、まず、すべての階層データが含まれた単一のデータセットを用意しておく必要があります。グループ化するアイテムとグループ化の基準に使用するアイテムには別々のフィールドを使用する必要があります。 たとえば、従業員をそれぞれのマネージャーの子として再帰的にまとめるデータセットには、従業員名、従業員 ID、マネージャー名、マネージャー ID などが含まれます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="to-create-a-recursive-hierarchy-group"></a>再帰型階層グループを作成するには  
  
1.  デザイン ビューで、テーブルを追加して、表示するデータセット フィールドをドラッグします。 通常、階層として表示する必要のあるフィールドは最初の列にあります。  
  
2.  テーブル内の任意の場所を右クリックして選択します。 選択したテーブルの詳細グループがグループ化ペインに表示されます。 行グループ ペインで、 **[詳細]**を右クリックし、 **[グループの編集]**をクリックします。 **[グループのプロパティ]** ダイアログ ボックスが表示されます。  
  
3.  **[グループ式]**の **[追加]**をクリックします。 新しい行がグリッドに表示されます。  
  
4.  **[グループ化の条件]** ボックスで、グループ化するフィールドを入力または選択します。  
  
5.  **[詳細設定]**をクリックします。  
  
6.  **[再帰的な親]** ボックスで、グループ化で親として使用するフィールドを入力または選択します。  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     レポートを実行します。 レポートに再帰型階層グループが表示されますが、階層を示すインデントはありません。  
  
## <a name="to-format-a-recursive-hierarchy-group-with-indent-levels"></a>再帰型階層グループにインデント レベルを設定するには  
  
1.  階層書式を表示するためのインデント レベルを追加する対象フィールドが含まれているテキスト ボックスをクリックします。 テキスト ボックスのプロパティがプロパティ ペインに表示されます。  
  
    > [!NOTE]  
    >  プロパティ ペインが表示されない場合は、 **[表示]** タブの **[プロパティ]** をクリックします。  
  
2.  プロパティ ウィンドウで、展開、 **Padding**ノード、 をクリックして**左**、ドロップダウン リストから選択し、 **\<式… >**です。  
  
3.  式ペインで次の式を入力します。  
  
     `=CStr(2 + (Level()*10)) + "pt"`  
  
     Padding のプロパティはすべて、 *nnyy*形式の文字列が必要です。ここで、 *nn* は数字、 *yy* は単位です。 この例の式では、 **Level** 関数を使用する文字列が構築され、再帰レベルに基づいて余白のサイズが増加されます。 たとえば、レベルが 1 の行では余白は 12 ポイント (2 + (1\*10)) に、レベルが 3 の行では 32 ポイント (2 + (3\*10)) になります。 **Level** 関数の詳細については、「 [Level](../../reporting-services/report-design/report-builder-functions-level-function.md)」を参照してください。  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     レポートを実行します。 グループ化されたデータの階層ビューがレポートに表示されます。  
  
## <a name="see-also"></a>参照  
 [再帰型階層グループ &#40; を作成します。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)   
 [フィルター、グループ、およびデータを並べ替える &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [集計関数リファレンス & #40 です。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md)   
 [テーブルと #40 です。レポート ビルダーおよび SSRS & #41 です。](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)   
 [マトリックスと #40 です。レポート ビルダーおよび SSRS & #41 です。](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)   
 [リストと #40 です。レポート ビルダーおよび SSRS & #41 です。](../../reporting-services/report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)   
 [テーブル、マトリックス、およびリスト & #40 です。レポート ビルダーおよび SSRS & #41 です。](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  

