---
title: 追加または削除のテーブルまたはビュー、データ ソース ビュー (Analysis Services) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.dsvdesigner.tablespane.f1
helpviewer_keywords:
- deleting tables
- tables [Analysis Services]
- removing tables
- adding tables
- data source views [Analysis Services], tables
- tables [Analysis Services], data source views
ms.assetid: 98307d04-6548-4d7d-9244-2371dd165249
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: f5bd0cf48e266149a0666b5e8d21d4d44efe41e3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074484"
---
# <a name="adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services"></a>データ ソース ビューでのテーブルまたはビューの追加または削除 (Analysis Services)
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でデータ ソース ビュー (DSV) を作成したら、テーブルおよび列を追加または削除することにより、データ ソース ビュー デザイナーでそれを変更できます。これには、別のデータ ソースからのテーブルと列の追加と削除も含まれます。  
  
 データ ソース ビュー デザイナーで DSV を開くには、ソリューション エクスプローラーで DSV をダブルクリックします。 DSV を開いたら、ボタン バーまたはメニューにある **[テーブルの追加と削除]** を使用して DSV を変更または拡張できます。 さらに、ダイアグラム内のオブジェクトを操作することもできます。 たとえば、オブジェクトを選択して、キーボードの Del キーを使用してそのオブジェクトを削除することができます。  
  
> [!WARNING]  
>  テーブルの削除は注意して行ってください。 テーブルを削除すると、関連する列およびリレーションシップのすべてが DSV から削除され、そのテーブルにバインドされているすべてのオブジェクトが無効になります。  
  
## <a name="selecting-tables-or-views-to-add-or-remove"></a>追加または削除するテーブルまたはビューの選択  
 **[テーブルの追加と削除]** ダイアログ ボックスを使用すると、 **[使用できるオブジェクト]** ボックスの一覧と **[含まれているオブジェクト]** ボックスの一覧の間でテーブルまたはビューを移動できます。 初期の **[使用できるオブジェクト]** ボックスの一覧には、まだデータ ソース ビューにないプライマリ データ ソースのテーブルまたはビューが含まれています。 プライマリ データ ソースのサポートしている場合、`OPENROWSET`関数の場合、プロジェクトまたはデータベースでは、他のデータ ソースから、テーブルまたはビューを追加することもできます。  
  
 DSV でのテーブルの追加または削除により、DSV で現在選択されているダイアグラムでもそのテーブルが追加または削除されます。 ダイアグラムの詳細については、次を参照してください。[データ ソース ビュー デザイナーでのダイアグラムの作業&#40;Analysis Services&#41;](work-with-diagrams-in-data-source-view-designer-analysis-services.md)です。  
  
 **[テーブルの追加と削除]** ダイアログ ボックスの **[含まれているオブジェクト]** ボックスの一覧にテーブルを移動すると、関連テーブルもすべて追加できるようになります。 データ ソース内に外部キー制約が存在する場合は、この操作により、制約に従ってテーブルが追加されます。 使用することが外部キー制約が存在しない場合、`NameMatchingCriteria`可能性の高いリレーションシップを生成するテーブル内の列名を照合する基準を指定する関係を識別するデータ ソース ビューのプロパティです。 場合、`NameMatchingCriteria`データ ソース ビューのプロパティを指定すると、をクリックして**関連テーブルの追加**を一致する列名を持つデータ ソースからテーブルを追加します。 設定の詳細については、`NameMatchingCriteria`プロパティを参照してください[多次元モデル内のデータ ソース ビュー](data-source-views-in-multidimensional-models.md)です。  
  
> [!NOTE]  
>  データ ソース ビューでオブジェクトの追加や削除を行っても、基になるデータ ソースは影響を受けません。  
  
## <a name="see-also"></a>参照  
 [多次元モデル内のデータ ソース ビュー](data-source-views-in-multidimensional-models.md)   
 [データ ソース ビュー デザイナーでのダイアグラムの作業&#40;Analysis Services&#41;](work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
  