---
title: 非表示にするか、列を固定 |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e588e16549a609fe15f0f7d7eaf89a010a5bde2c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="hide-or-freeze-columns"></a>非表示にするか、列を固定 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  モデル デザイナーで、テーブルに表示する必要のない列がある場合は、一時的に非表示にすることができます。 列を非表示にすると画面上のスペースが広くなり、新しい列の追加や、必要なデータ列のみを対象とした作業を行いやすくなります。 列の非表示と再表示は、モデル デザイナーの **[列]** メニューおよび各列見出しで使用できる右クリック メニューのどちらからでも行うことができます。 モデルのある領域を表示したまま、別の領域にスクロールするには、表示しておく領域内の特定の列を固定します。  
  
> [!IMPORTANT]  
>  列を非表示にする機能はデータ セキュリティを目的としたものではなく、モデル デザイナーまたはレポートの列の一覧を簡略化し、短縮して表示するだけのためのものでもありません。 データを保護するには、セキュリティ ロールを定義することができます。 ロールは、表示することができるメタデータとデータを、ロールで定義されたオブジェクトのみに制限できます。 詳細については、次を参照してください。[ロール](../../analysis-services/tabular-models/roles-ssas-tabular.md)です。  
  
 列を非表示にする場合、モデル デザイナーまたはレポートでの作業中に列を非表示にするかどうかを選択できます。 すべての列を非表示にすると、モデル デザイナーのテーブル全体が空白になります。  
  
> [!NOTE]  
>  非表示にする列が多い場合は、列の表示と非表示を切り替える代わりにパースペクティブを作成する方法もあります。 パースペクティブは、データのカスタム ビューです。関連するデータのサブセットを容易に扱うことができます。 詳細については、次を参照してください[管理パースペクティブの作成および。](../../analysis-services/tabular-models/create-and-manage-perspectives-ssas-tabular.md)  
  
### <a name="to-hide-an-individual-column"></a>列を個別に非表示にするには  
  
1.  モデル デザイナーで、非表示にする列が含まれるテーブルを選択します。  
  
2.  列を右クリックして **[列を表示しない]** をクリックし、 **[デザイナーとレポートから]**、 **[レポートから]**、 **[デザイナーから]** のいずれかをクリックします。  
  
### <a name="to-hide-multiple-columns"></a>複数の列を非表示にするには  
  
1.  モデル デザイナーで、非表示にする列が含まれるテーブルを選択します。  
  
2.  **[列]** メニューをクリックし、 **[表示/非表示]** をクリックします。  
  
3.  **[列の表示/非表示]** ダイアログ ボックスで、非表示にする各列を見つけ、 **[デザイナーで]** と **[レポートで]** の一方または両方の選択を解除します。  
  
4.  **[OK]** をクリックします。  
  
### <a name="to-freeze-columns"></a>列を固定するには  
  
1.  モデル デザイナーで、固定する列が含まれるテーブルを選択します。  
  
2.  固定する 1 つ以上の列を選択します。  
  
3.  **[列]** メニューをクリックし、 **[固定]** をクリックします。  
  
    > [!NOTE]  
    >  固定された列は、デザイナーのテーブルの左側 (前) に移動されます。 列の固定を解除しても、元の場所には戻りません。  
  
## <a name="see-also"></a>参照  
 [テーブルと列](../../analysis-services/tabular-models/tables-and-columns-ssas-tabular.md)   
 [パースペクティブ](../../analysis-services/tabular-models/perspectives-ssas-tabular.md)   
 [Roles](../../analysis-services/tabular-models/roles-ssas-tabular.md)  
  
  
