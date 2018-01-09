---
title: "非表示にする列または固定 (SSAS テーブル) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.asvs.bidtoolset.hideunhidecolumnsdb.f1
ms.assetid: 5407aee5-6a07-4559-a2ba-2ca00a242f02
caps.latest.revision: "10"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8334a3e6087740a2060425e764e9de6afa365e19
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="hide-or-freeze-columns-ssas-tabular"></a>列の非表示または固定 (SSAS テーブル)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]モデル デザイナーで、テーブルに表示する列がある場合を一時的に非表示にできます。 列を非表示にすると画面上のスペースが広くなり、新しい列の追加や、必要なデータ列のみを対象とした作業を行いやすくなります。 列の非表示と再表示は、モデル デザイナーの **[列]** メニューおよび各列見出しで使用できる右クリック メニューのどちらからでも行うことができます。 モデルのある領域を表示したまま、別の領域にスクロールするには、表示しておく領域内の特定の列を固定します。  
  
> [!IMPORTANT]  
>  列を非表示にする機能はデータ セキュリティを目的としたものではなく、モデル デザイナーまたはレポートの列の一覧を簡略化し、短縮して表示するだけのためのものでもありません。 データを保護するには、セキュリティ ロールを定義することができます。 ロールは、表示することができるメタデータとデータを、ロールで定義されたオブジェクトのみに制限できます。 詳細については、「 [ロール (SSAS テーブル)](../../analysis-services/tabular-models/roles-ssas-tabular.md)」を参照してください。  
  
 列を非表示にする場合、モデル デザイナーまたはレポートでの作業中に列を非表示にするかどうかを選択できます。 すべての列を非表示にすると、モデル デザイナーのテーブル全体が空白になります。  
  
> [!NOTE]  
>  非表示にする列が多い場合は、列の表示と非表示を切り替える代わりにパースペクティブを作成する方法もあります。 パースペクティブは、データのカスタム ビューです。関連するデータのサブセットを容易に扱うことができます。 詳細については、「[Create and Manage Perspectives (SSAS Tabular)](../../analysis-services/tabular-models/create-and-manage-perspectives-ssas-tabular.md)」(パースペクティブの作成と管理 (SSAS テーブル)) を参照してください。  
  
### <a name="to-hide-an-individual-column"></a>列を個別に非表示にするには  
  
1.  モデル デザイナーで、非表示にする列が含まれるテーブルを選択します。  
  
2.  列を右クリックして **[列を表示しない]**をクリックし、 **[デザイナーとレポートから]**、 **[レポートから]**、 **[デザイナーから]**のいずれかをクリックします。  
  
### <a name="to-hide-multiple-columns"></a>複数の列を非表示にするには  
  
1.  モデル デザイナーで、非表示にする列が含まれるテーブルを選択します。  
  
2.  **[列]** メニューをクリックし、 **[表示/非表示]**をクリックします。  
  
3.  **[列の表示/非表示]** ダイアログ ボックスで、非表示にする各列を見つけ、 **[デザイナーで]** と **[レポートで]**の一方または両方の選択を解除します。  
  
4.  **[OK]** をクリックします。  
  
### <a name="to-freeze-columns"></a>列を固定するには  
  
1.  モデル デザイナーで、固定する列が含まれるテーブルを選択します。  
  
2.  固定する 1 つ以上の列を選択します。  
  
3.  **[列]** メニューをクリックし、 **[固定]**をクリックします。  
  
    > [!NOTE]  
    >  固定された列は、デザイナーのテーブルの左側 (前) に移動されます。 列の固定を解除しても、元の場所には戻りません。  
  
## <a name="see-also"></a>参照  
 [テーブルと列 &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/tables-and-columns-ssas-tabular.md)   
 [パースペクティブ (SSAS テーブル)](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [ロール (SSAS テーブル)](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  
