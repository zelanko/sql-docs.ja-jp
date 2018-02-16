---
title: "データ ソース ビュー (Analysis Services) で論理主キーの定義 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- removing logical primary keys
- logical primary keys [SQL Server]
- deleting logical primary keys
- data source views [Analysis Services], logical primary keys
ms.assetid: 172bc267-c637-4caa-bf55-0ba198d30b1e
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: ab3e26fdddc257e2ddf8edd450c412bbabb7c557
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="define-logical-primary-keys-in-a-data-source-view-analysis-services"></a>データ ソース ビューでの論理主キーの定義 (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
データ ソース ビュー ウィザードとデータ ソース ビュー デザイナーでは、データベース テーブルから生成されたデータ ソース ビューにテーブルを追加した場合、そのテーブルの主キーが自動的に定義されます。  
  
 場合によっては、データ ソース ビューの主キーは手動で定義しなければならない場合があります。 たとえば、パフォーマンスまたは設計上の理由から、データ ソース内のテーブルに主キー列が明示的に定義されていない場合があります。 名前付きクエリおよびビューでも、テーブルの主キー列が省略されることがあります。 テーブル、ビュー、または名前付きクエリに物理主キーが定義されていない場合は、データ ソース ビュー デザイナーでテーブル、ビュー、または名前付きクエリの論理主キーを手動で定義できます。  
  
## <a name="set-a-logical-primary-key"></a>論理主キーの設定  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、テーブル内のレコードの一意の識別、ディメンション テーブル内のキー列の識別、テーブル、ビュー、および名前付きクエリ間のリレーションシップのサポートのために主キーが必要になります。 これらのリレーションシップを使用して、基になるデータ ソースからデータやメタデータを取得するためのクエリを作成したり、高度なビジネス インテリジェンス機能を活用したりできます。  
  
 論理主キーには、名前付き計算を含む、任意の列を使用できます。 論理主キーを作成すると、データ ソース ビューに一意の制約が作成され、主キー制約として設定されます。 選択したテーブルで指定されている他の既存の論理主キーは削除されます。  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でプロジェクトを開くか、論理主キーを設定するデータ ソース ビューが含まれているデータベースに接続します。  
  
2.  ソリューション エクスプローラーで、 **[データ ソース ビュー]** フォルダーを展開し、データ ソース ビューをダブルクリックします。  
  
     テーブルまたはビューを検索するには、 **[データ ソース ビュー]** メニューをクリックするか、 **テーブル**  ペインまたは **ダイアグラム** ペインの空いている領域を右クリックして、 **[テーブルの検索]** をクリックします。  
  
3.  **テーブル** ペインまたは **ダイアグラム** ペインで、論理主キーの定義に使用する列を右クリックし、 **[論理主キーの設定]**をクリックします。  
  
     論理主キーを設定するオプションは、主キーを持たないテーブルにのみ使用できます。  
  
     これで、キーの設定後、キー アイコンによって主キー列を識別できるようになりました。  
  
## <a name="see-also"></a>参照  
 [多次元モデル内のデータ ソース ビュー](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [データ ソース ビュー &#40; での名前付き計算を定義します。Analysis Services &#41;](../../analysis-services/multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
  
