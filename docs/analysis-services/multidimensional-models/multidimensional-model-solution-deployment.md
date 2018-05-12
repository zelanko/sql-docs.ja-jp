---
title: 多次元モデル ソリューションの配置 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4e5f4b4f7f30ec9f94993e34596d348ae22842fd
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="multidimensional-model-solution-deployment"></a>多次元モデルのソリューションの配置
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの開発を完了したら、Analysis Services サーバーにデータベースを配置できます。 Analysis Services には、テスト サーバーまたは実稼働サーバーにデータベースを移動するために使用できる 6 つの配置方法が用意されています。 ここでは、それらの方法を効果の大きいものから、AMO オートメーション、XMLA、配置ウィザード、配置ユーティリティ、同期ウィザード、バックアップおよび復元の順に説明します。  
  
 このトピックのセクションは次のとおりです。  
  
 [配置方法](#bkmk_meth)  
  
 [配置に関する考慮事項](#bkmk_considerations)  
  
 [関連タスク](#bkmk_rel)  
  
##  <a name="bkmk_meth"></a> 配置方法  
  
|方法|Description|リンク|  
|------------|-----------------|----------|  
|**分析管理オブジェクト (AMO) オートメーション**|AMO を使用すると、ソリューションの配置に使用できるコマンドを含む、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の完全なコマンド セットのプログラム インターフェイスを利用できます。 ソリューション配置の方法として最も柔軟に使用できるのは、AMO オートメーションですが、この方法ではプログラミング作業も必要になります。  AMO を使用する主な利点は、AMO アプリケーションでは SQL Server エージェントを使用して、あらかじめ設定したスケジュールに従って配置を実行できることです。|[分析管理オブジェクト & #40; を使用した開発AMO & #41;](../../analysis-services/multidimensional-models/analysis-management-objects/developing-with-analysis-management-objects-amo.md)|  
|**XMLA**|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、既存の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースのメタデータの XMLA スクリプトを生成し、別のサーバーでそのスクリプトを実行して初期データベースを再作成します。 XMLA スクリプトは、配置プロセスを定義し、それをコード化して XMLA スクリプトに保存することにより、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で簡単に作成できます。 XMLA スクリプトをファイルに保存すると、簡単に、スケジュールに基づいてスクリプトを実行したり、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のインスタンスに直接接続しているアプリケーションにスクリプトを埋め込んだりすることができます。<br /><br /> SQL Server エージェントを使用すると、XMLA スクリプトもあらかじめ設定したスケジュールに従って実行できますが、XMLA スクリプトには AMO ほどの柔軟性はありません。 AMO では、さまざまなすべての管理コマンドをホストすることにより、広範にわたる機能を実現しています。|[XMLA を使用したモデル ソリューションを配置します。](../../analysis-services/multidimensional-models/deploy-model-solutions-using-xmla.md)|  
|**配置ウィザード**|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトによって生成された XMLA 出力ファイルを使用して、プロジェクトのメタデータを宛先サーバーに配置するには、配置ウィザードを使用します。 配置ウィザードを使用すると、プロジェクト ビルドの出力ディレクトリによって作成される [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ファイルからインスタンスを直接配置できます。<br /><br /> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の配置ウィザードを使用する主な利点は利便性です。 後で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で使用するために XMLA スクリプトを保存できるのと同様に、配置ウィザード スクリプトも保存できます。 配置ウィザードは、対話的に実行することも、配置ユーティリティを使用してコマンド プロンプトから実行することもできます。|[配置ウィザードを使用したモデル ソリューションを配置します。](../../analysis-services/multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md)|  
|**配置ユーティリティ**|配置ユーティリティを使用すると、コマンド プロンプトから Analysis Services の配置エンジンを起動することができます。|[配置ユーティリティを使用してモデル ソリューションを配置します。](../../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)|  
|**データベースの同期ウィザード**|2 つの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース間でメタデータとデータを同期するには、データベースの同期ウィザードを使用します。<br /><br /> 同期ウィザードを使用すると、コピー元のサーバーからコピー先のサーバーにデータとメタデータをコピーできます。 配置するデータベースのコピーが、コピー先のサーバーにない場合、新しいデータベースがコピー先のサーバーにコピーされます。 コピー先のサーバーに同じデータベースのコピーが既にある場合、コピー先サーバー上のデータベースは、ソース データベースのメタデータとデータを使用するように更新されます。|[Analysis Services データベースを同期します。](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)|  
|**バックアップと復元**|バックアップは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを転送する最も簡単な方法です。 **[バックアップ]** ダイアログ ボックスを使用すると、オプション構成を設定した後で、ダイアログ ボックスから直接バックアップを実行できます。 また、スクリプトを作成して保存し、必要なときに実行することもできます。<br /><br /> バックアップと復元は、他の配置方法ほど頻繁には使用されませんが、インフラストラクチャの要件を最小限に抑えながら配置をすばやく完了することができます。|[Analysis Services データベースのバックアップと復元](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)|  
  
##  <a name="bkmk_considerations"></a> 配置に関する考慮事項  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを配置する前に、次のどの質問がソリューションに当てはまるかを検討し、関連するリンクを参照して問題の解決方法を確認してください。  
  
|考慮事項|詳細情報へのリンク|  
|-------------------|------------------------------|  
|このソリューションにはどのようなハードウェアおよびソフトウェア リソースが必要か。|[要件と Analysis Services の配置に関する考慮事項](../../analysis-services/multidimensional-models/requirements-and-considerations-for-analysis-services-deployment.md)|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のパッケージ、レポート、リレーショナル データベース スキーマなど、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトの範囲外にある関連オブジェクトをどのように配置するか。||  
|配置した [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースでデータをどのように読み込んで更新するか。<br /><br /> 配置した [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース内のメタデータ (計算など) をどのように更新するか。|このトピックの「[配置方法](#bkmk_meth) 」を参照してください。|  
|インターネット経由での [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データへのアクセスをユーザーに許可するか。|[インターネット インフォメーション サービス (&) #40";"IIS"&"#41 です。 Analysis Services への HTTP アクセスを構成します。8.0](../../analysis-services/instances/configure-http-access-to-analysis-services-on-iis-8-0.md)|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データへの連続クエリ アクセスを提供するか。|[要件と Analysis Services の配置に関する考慮事項](../../analysis-services/multidimensional-models/requirements-and-considerations-for-analysis-services-deployment.md)|  
|リンクされているオブジェクトまたはリモート パーティションを使用して、分散環境にオブジェクトを配置するか。|[ローカル パーティションの作成と管理 (Analysis Services)](../../analysis-services/multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)[リモート パーティションの作成と管理 (Analysis Services)](../../analysis-services/multidimensional-models/create-and-manage-a-remote-partition-analysis-services.md) および [リンク メジャー グループ](../../analysis-services/multidimensional-models/linked-measure-groups.md)。|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データをどのように保護するか。|[オブジェクトと操作 & #40; への認証のアクセスAnalysis Services & #41;](../../analysis-services/multidimensional-models/authorizing-access-to-objects-and-operations-analysis-services.md)|  
  
##  <a name="bkmk_rel"></a> 関連タスク  
 [要件と Analysis Services の配置に関する考慮事項](../../analysis-services/multidimensional-models/requirements-and-considerations-for-analysis-services-deployment.md)  
  
 [XMLA を使用したモデル ソリューションを配置します。](../../analysis-services/multidimensional-models/deploy-model-solutions-using-xmla.md)  
  
 [配置ウィザードを使用したモデル ソリューションを配置します。](../../analysis-services/multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md)  
  
 [配置ユーティリティを使用してモデル ソリューションを配置します。](../../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)  
  
  
