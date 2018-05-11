---
title: 追加または削除のテーブルまたはビュー、データ ソース ビュー (Analysis Services) |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2a51b3ecadebebc7beceddbee4cbae948b0bcd82
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services"></a>データ ソース ビューでのテーブルまたはビューの追加または削除 (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でデータ ソース ビュー (DSV) を作成したら、テーブルおよび列を追加または削除することにより、データ ソース ビュー デザイナーでそれを変更できます。これには、別のデータ ソースからのテーブルと列の追加と削除も含まれます。  
  
 データ ソース ビュー デザイナーで DSV を開くには、ソリューション エクスプローラーで DSV をダブルクリックします。 DSV を開いたら、ボタン バーまたはメニューにある **[テーブルの追加と削除]** を使用して DSV を変更または拡張できます。 さらに、ダイアグラム内のオブジェクトを操作することもできます。 たとえば、オブジェクトを選択して、キーボードの Del キーを使用してそのオブジェクトを削除することができます。  
  
> [!WARNING]  
>  テーブルの削除は注意して行ってください。 テーブルを削除すると、関連する列およびリレーションシップのすべてが DSV から削除され、そのテーブルにバインドされているすべてのオブジェクトが無効になります。  
  
## <a name="selecting-tables-or-views-to-add-or-remove"></a>追加または削除するテーブルまたはビューの選択  
 **[テーブルの追加と削除]** ダイアログ ボックスを使用すると、 **[使用できるオブジェクト]** ボックスの一覧と **[含まれているオブジェクト]** ボックスの一覧の間でテーブルまたはビューを移動できます。 初期の **[使用できるオブジェクト]** ボックスの一覧には、まだデータ ソース ビューにないプライマリ データ ソースのテーブルまたはビューが含まれています。 プライマリ データ ソースが **OPENROWSET** 機能をサポートしている場合は、プロジェクトまたはデータベースの他のデータ ソースからテーブルまたはビューを追加することもできます。  
  
 DSV でのテーブルの追加または削除により、DSV で現在選択されているダイアグラムでもそのテーブルが追加または削除されます。 ダイアグラムの詳細については、「 [データ ソース ビュー デザイナーでのダイアグラムの操作 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)」を参照してください。  
  
 **[テーブルの追加と削除]** ダイアログ ボックスの **[含まれているオブジェクト]** ボックスの一覧にテーブルを移動すると、関連テーブルもすべて追加できるようになります。 データ ソース内に外部キー制約が存在する場合は、この操作により、制約に従ってテーブルが追加されます。 外部キー制約が存在しない場合は、データ ソース ビューの **NameMatchingCriteria** プロパティを使用して、リレーションシップを指定できます。指定するには、テーブル内の列名の一致基準を指定してリレーションシップを生成します。 データ ソース ビューに **NameMatchingCriteria**プロパティが指定されている場合は、 **[関連テーブルの追加]** をクリックして、一致する列名を持つデータ ソースからテーブルを追加します。 **NameMatchingCriteria** プロパティの設定の詳細については、「 [多次元モデル内のデータ ソース ビュー](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)」を参照してください。  
  
> [!NOTE]  
>  データ ソース ビューでオブジェクトの追加や削除を行っても、基になるデータ ソースは影響を受けません。  
  
## <a name="see-also"></a>参照  
 [多次元モデル内のデータ ソース ビュー](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [データ ソース ビュー デザイナー & #40; でのダイアグラムの操作します。Analysis Services & #41;](../../analysis-services/multidimensional-models/work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  
