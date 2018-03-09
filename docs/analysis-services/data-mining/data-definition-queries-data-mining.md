---
title: "データ定義クエリ (データ マイニング) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49e02de1-4ffa-401c-8eee-471a9c25b86a
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 286d7cbe5d6dbb2fb0b05b937fbd1a304f89aa1e
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="data-definition-queries-data-mining"></a>データ定義クエリ (データ マイニング)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
データ マイニングの *データ定義クエリ* というカテゴリは、次の処理を実行する DMX ステートメントまたは XMLA コマンドを意味します。  
  
-   データ マイニング オブジェクト (モデルなど) の作成、変更、または操作  
  
-   トレーニングまたは予測で使用されるデータのソースの定義  
  
-   マイニング モデルとマイニング構造のエクスポートまたはインポート  
  
 [データ定義クエリの作成](#bkmk_Create)  
  
-   [SQL Server データ ツールでのデータ定義クエリ](#bkmk_ssdt)  
  
-   [SQL Server Management Studio でのデータ定義クエリ](#bkmk_SSMS)  
  
 [データ定義ステートメントのスクリプト化](#bkmk_Scripts)  
  
 [データ定義ステートメントのスクリプト化](#bkmk_Export)  
  
##  <a name="bkmk_Create"></a> データ定義クエリの作成  
 DMX を使用して手動でクエリを作成する以外に、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] および [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の予測クエリ ビルダーを使用するか、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の DMX クエリ ウィンドウを使用して、データ定義クエリ (ステートメント) を作成できます。 DMX でのデータ定義ステートメントは、Analysis Services データ定義言語 (DDL) の一部です。  
  
 特定のデータ定義ステートメントの構文の詳細については、「[データ マイニング拡張機能 (DMX) リファレンス](../../dmx/data-mining-extensions-dmx-reference.md)」を参照してください。  
  
###  <a name="bkmk_ssdt"></a> SQL Server データ ツールでのデータ定義クエリ  
 データ マイニング ウィザードは、マイニング モデルやマイニング構造の作成および変更、予測クエリで使用されるデータ ソースの定義、およびトレーニングに適した [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のツールです。  
  
 ただし、データ構造またはマイニング モデルを作成するためにウィザードによってサーバーに送信されるステートメントを確認するには、SQL Server Profiler を使用してデータ定義ステートメントをキャプチャできます。 詳細については、「 [SQL Server Profiler を使用した Analysis Services の監視](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md)」を参照してください。  
  
 トレーニングまたは予測に使用されるデータ ソースの定義に使用されるステートメントを表示するには、予測クエリ ビルダーの **[SQL ビュー]** を使用できます。 場合によっては、トレーニングとモデルのテストのために、予測クエリ ビルダーを使用して基本的なクエリを作成すると、正しい構文を確実に使用することができ役に立ちます。 その後、 **[SQL ビュー]** に切り替えて、手動でクエリを編集できます。 詳細については、「 [手動での予測クエリの編集](../../analysis-services/data-mining/manually-edit-a-prediction-query.md)」を参照してください。  
  
###  <a name="bkmk_SSMS"></a> SQL Server Management Studio でのデータ定義クエリ  
 データ マイニング オブジェクトでは、データ定義クエリを使用して次の操作を実行できます。  
  
-   特定の種類のモデル (クラスター モデルまたはデシジョン ツリー モデル) の作成。[CREATE MINING MODEL (DMX)](../../dmx/create-mining-model-dmx.md) を使用します。  
  
-   モデルの追加または列の変更による、既存のマイニング構造の変更。[ALTER MINING STRUCTURE (DMX)](../../dmx/alter-mining-structure-dmx.md) を使用します。 DMX を使用してマイニング モデルを変更できないことに注意してください。既存の構造に新しいモデルを追加できるだけです。  
  
-   マイニング モデルのコピー作成とその変更。[SELECT INTO (DMX)](../../dmx/select-into-dmx.md) を使用します。  
  
-   モデルのトレーニングに使用されるデータ セットの定義。[INSERT INTO (DMX)](../../dmx/insert-into-dmx.md) をデータ ソース クエリ (OPENROWSET など) と共に使用します。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で提供されるクエリ テンプレートは、データ定義クエリを作成するときに役立ちます。 詳細については、「 [SQL Server Management Studio での Analysis Services テンプレートの使用](../../analysis-services/instances/use-analysis-services-templates-in-sql-server-management-studio.md)」を参照してください。  
  
 通常、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] に提供されるテンプレートには一般的な構文定義しか含まれないため、 **[クエリ]** ウィンドウに入力するか、パラメーターを入力するために表示されるダイアログ ボックスを使用して、定義をカスタマイズする必要があります。  
  
 インターフェイスを利用してパラメーターを入力する方法の例については、「 [テンプレートからの単一予測クエリの作成](../../analysis-services/data-mining/create-a-singleton-prediction-query-from-a-template.md)」を参照してください。  
  
###  <a name="bkmk_Scripts"></a> データ定義ステートメントのスクリプト化  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では複数のスクリプト言語およびプログラム言語が提供され、データ マイニング オブジェクトの作成または変更、あるいはデータ ソースの定義に使用できます。  DMX はデータ マイニング タスクの高速化を目的としていますが、XMLA と AMO の両方も、スクリプトまたはカスタム モードでオブジェクトを操作するために使用できます。  
  
 Excel データ マイニング アドインにも多くのクエリ テンプレートが含まれます。複雑な DMX ステートメントを作成するための **[詳細クエリ エディター]**も提供されます。 クエリを対話形式で作成してから、[SQL ビュー] に切り替えて DMX ステートメントをキャプチャできます。  
  
##  <a name="bkmk_Export"></a> モデルのエクスポートおよびインポート  
 DMX のデータ定義ステートメントを使用して、モデルの定義、必要な構造、およびデータ ソースをエクスポートすることができます。その後、その定義を別のサーバーにインポートできます。 エクスポートとインポートの使用は、データ マイニング モデルとマイニング構造を [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンス間で移動するための最も速くて容易な方法です。 詳細については、「 [データ マイニング ソリューションおよびオブジェクトの管理](../../analysis-services/data-mining/management-of-data-mining-solutions-and-objects.md)」を参照してください。  
  
> [!WARNING]  
>  モデルがキューブ データ ソースのデータに基づいている場合は、モデルをエクスポートするために DMX を使用できません。代わりにバックアップと復元を使用してください。  
  
##  <a name="bkmk_Tasks"></a> 関連タスク  
 次の表に、データ定義クエリに関連するタスクへのリンクを示します。  
  
|||  
|-|-|  
|DMX クエリ用のテンプレートの使用|[SQL Server Management Studio で Analysis Services テンプレートを使用します。](../../analysis-services/instances/use-analysis-services-templates-in-sql-server-management-studio.md)|  
|予測クエリ ビルダーを使用した、あらゆる種類のクエリの設計|[予測クエリ ビルダーを使用して予測クエリを作成します。](../../analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)|  
|SQLServer Profiler を使用したクエリ定義のキャプチャ、および [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を監視するためのトレースの使用|[SQL Server Profiler を使用して、Analysis Services の監視を](../../analysis-services/instances/use-sql-server-profiler-to-monitor-analysis-services.md)|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] で提供されるスクリプト言語やプログラム言語の詳細|[XML for Analysis &#40;です。XMLA &#41;参照](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)<br /><br /> [分析管理オブジェクト &#40; を使用した開発AMO &#41;](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)|  
|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] および [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] でのモデルの管理の詳細。|[エクスポートし、インポートのデータ マイニング オブジェクト](../../analysis-services/data-mining/export-and-import-data-mining-objects.md)<br /><br /> [エクスポート &#40;DMX&#41;](../../dmx/export-dmx.md)<br /><br /> [インポート &#40;DMX&#41;](../../dmx/import-dmx.md)|  
|OPENROWSET、および外部データへのクエリのための他の方法の詳細|[<ソース データ クエリ>](../../dmx/source-data-query.md)|  
  
## <a name="see-also"></a>参照  
 [データ マイニング ウィザードと &#40; です。Analysis Services - データ マイニング &#41; です。](../../analysis-services/data-mining/data-mining-wizard-analysis-services-data-mining.md)  
  
  
