---
title: "データ サイエンスのシナリオとソリューション テンプレート |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/22/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to: SQL Server 2016
ms.assetid: 49e54fa9-9b28-44ba-b256-06dad4e8dece
caps.latest.revision: "17"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 3c180282735da59d8d3dfa039e70d0eea5ebd7e5
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="data-science-scenarios-and-solution-templates"></a>データ サイエンスのシナリオとソリューション テンプレート

テンプレートは、ソリューションを短時間で実装するために役立つベスト プラクティスを示し、構成要素を提供するサンプル ソリューションです。 各テンプレートは、特定の垂直方向または業界の特定の問題を解決するために設計されています。 各テンプレートのタスクは、データ準備や機能エンジニアリングから、モデルのトレーニングとスコアリングまで、多岐にわたります。 については、これらのテンプレートを使用してどのように[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]動作します。 次に、自由に独自のシナリオに合わせてソリューションをビルドするカスタム テンプレートをカスタマイズします。 

各ソリューションには、サンプル データ、R コード、または Python コードが含まれていて、該当する場合、SQL ストアド プロシージャです。 コードは、SQL Server 上での計算で、優先される R、Python または開発環境で実行できます。 場合によっては、T-SQL と SQL Server Management Studio など、任意の SQL クライアント ツールを使用して直接コードを実行できます。

> [!TIP]
> 
> テンプレートのほとんどは、オンプレミス在庫の両方をサポートする複数のバージョンであり、機械学習のためのプラットフォームのクラウドです。 たとえば、SQL Server のみを使用してソリューションをビルドすることができます。 または Microsoft R サーバーか、Azure Machine Learning でソリューションをビルドすることができます。

+ 詳細と更新プログラムは、このお知らせを参照してください: [Azure ML で新しいテンプレートの画期的な](https://blogs.technet.microsoft.com/machinelearning/2015/04/09/exciting-new-templates-in-azure-ml/)

+ ダウンロードとセットアップ手順は、次を参照してください。[テンプレートを使用する方法](#bkmk_HowTo)です。

## <a name="fraud-detection"></a>不正行為の検出

[オンライン不正検出テンプレート (SQL Server R Services)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/FraudDetection/Introduction.md)

**新機能:**不正な処理を検出する機能は、オンライン ビジネスにとって重要です。 チャージ バックの損失を減らすためには、企業は迅速に盗まれた支払い方法または資格情報を使用して作成されたトランザクションを識別する必要があります。 不正な取引が検出された場合、通常、それ以上の損失を防ぐために、できるだけ早く特定のアカウントをブロックする措置を取ります。 このシナリオでは、オンラインで購入トランザクションからのデータを使用して、可能性の高い不正行為を特定する方法を学習します。

**方法:**不正行為の検出は、二項分類の問題と解決されます。 このテンプレートに使用する手法は、他のドメインの不正行為の検出にも簡単に適用できます。


## <a name="campaign-optimization"></a>キャンペーンの最適化

[予測する方法とタイミング潜在顧客に連絡するには](https://microsoft.github.io/r-server-campaign-optimization/)

**新機能:**このソリューションでは、潜在顧客の人口統計、履歴応答データ、および製品固有の詳細情報に基づくを予測する保険業界のデータを使用します。  推奨設定が最適なチャネルと購買行動に影響するアプローチのユーザーに時刻を示すために生成されます。

**方法:**ソリューションを作成し、複数のモデルを比較します。 ソリューションでは、自動データ統合およびストアド プロシージャを使用してデータの準備も示します。 SQL Server データベース内、Azure HDInsight Spark での並列の例が提供されます。 

## <a name="health-care-predict-length-of-stay-in-hospital"></a>健康保険: 病院の維持の長さの予測 

[病院の維持の長さを予測します。](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

**新機能:**注意および計画の重要な部分は、正確に予測する患者が長期的な入院を必要があります。 管理者は、どの機能が他のリソースを必要と判断する必要があるし、受ける保証患者のニーズを満たしていることができます。

**方法:**このソリューションは、データ サイエンス仮想マシンを使用して、有効になっている機械学習で SQL Server のインスタンスが含まれています。 配置済みモデルとの対話に使用できる Power BI レポートのセットも含まれています。

## <a name="customer-churn"></a>顧客チャーン

[顧客チャーン予測テンプレート (SQL Server R Services)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/Churn/Introduction.md)

**新機能:**データを分析して予測顧客チャーンが重要では、業界の競合するお客様の損失を管理および防止する必要があります: 銀行、通信、および製品版には、いくつかの例です。 顧客離れ分析の目標は、離れる可能性が高い顧客を特定し、そのような顧客が離れないようにして、ビジネスを維持することです。

**方法:**このテンプレートを作成、チャーン問題として、**二項分類**問題です。 顧客層と顧客トランザクションという 2 つのソースからサンプル データを使用し、顧客離れを起こす可能性が高い顧客と低い顧客を分類します。
  
## <a name="predictive-maintenance"></a>予測メンテナンス

[予測的なメンテナンス テンプレート (SQL Server 2016)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/PredictiveMaintenance/Introduction.md)

**新機能:**予測的なメンテナンスの目的は、過去のエラーをキャプチャし、デバイスが失敗するタイミングと場所を予測する情報を使用することによりメンテナンス タスクの効率を向上させる。 デバイスの陳腐化を予測する機能は、分散データやセンサーに依存するアプリケーションに対して特に有効です。 このメソッドは、監視または IoT (モ ノのインターネット) デバイスでエラーを予測にも適用できませんでした。

詳細については、このお知らせを参照してください:[新しい予測メンテナンス テンプレート](https://blogs.technet.microsoft.com/machinelearning/2015/04/09/exciting-new-templates-in-azure-ml/)

**方法:** 「場合は、サービスが提供されてマシン失敗しますか?」、質問に答えることでこのソリューションに焦点を当てています 入力データは、航空機のエンジン用にシミュレートされているセンサーの測定値を示します。 エンジンの現在の操作などの条件、現在の作業のサイクル、設定、およびセンサーの測定を監視から取得したデータを使用して、次の 3 つの種類の予測モデルを作成します。

-   **回帰モデル**: エンジンにエラーが発生するまでの時間を予測します。 サンプル モデルでは、「残り有効期間」(RUL)、「時間に失敗しました」(TTF) とも呼ばれるメトリックを予測します。
  
-   **分類モデル**: エンジンのエラーが発生する確率が高いかどうかを予測します。
  
    **二項分類モデル**エンジンは、一定期間内で失敗を予測します。

    **多クラス分類モデル**予測するかどうか特定のエンジン失敗したり、エラーの可能性の高い時間枠を提供します。 たとえば、特定の日について、指定した日、または指定した日から何日後に任意のデバイスでエラーが発生する可能性が高いかどうかを予測できます。

## <a name="energy-demand-forecasting"></a>エネルギーの需要予測

[エネルギーの需要と SQL Server R サービス テンプレートを予測](https://gallery.cortanaintelligence.com/Tutorial/Energy-Demand-Forecast-Template-with-SQL-Server-R-Services-1)

**新機能:**: エネルギー、量販店、およびサービスを含むさまざまなドメイン内の重要な問題は、需要予測します。 正確な需要を予測すると、企業の向上の生産計画、リソースの割り当てなどを実行して、その他の重要なビジネスの意思決定が役立ちます。 エネルギー セクターの需要予測エネルギー記憶域のコストを削減し、供給と需要を分散にとって重要です。

**方法:**このテンプレートでは、SQL Server R Services を使用して、電力の需要を予測します。 予測に使用するモデルは、ランダム フォレスト回帰モデルに基づく**rxDForest**高性能な機械学習アルゴリズムで Microsoft R Server に付属します。 このソリューションには、需要シミュレーター、モデルのトレーニングに必要なすべての R コードと T-SQL コード、予測の生成とレポートに使用できるストアド プロシージャが含まれています。 


## <a name="bkmk_HowTo"></a>テンプレートを使用する方法

各テンプレートに含まれるファイルをダウンロードするには、GitHub コマンドを使用するか、リンクを開いて **[Download Zip (Zip ファイルをダウンロード)]** をクリックし、すべてのファイルをコンピューターに保存します。  通常、ダウンロードしたソリューションには次のフォルダーが含まれています。
  
-   **Data**: 各アプリケーションのサンプル データが含まれています。
  
-   **R**: このソリューションに必要なすべての R 開発コードが含まれています。 このソリューションには、Microsoft R Server に含まれるライブラリが必要ですが、任意の R IDE で開き、編集することができます。 この R コードは、SQL Server インスタンスに対する計算コンテキストを設定し、計算が "データベース内で" 実行されるように最適化されています。
  
-   **SQLR**: [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] などの SQL 環境で実行して、データ処理、機能エンジニアリング、モデルの展開など、関連するタスクを実行するストアド プロシージャを作成できる複数の .sql ファイルが含まれています。
  
    このフォルダーには、すべてのスクリプトを呼び出し、包括的な環境を作成できる PowerShell スクリプトも含まれています。 スクリプトは、必ず実際の環境似合わせて編集してください。

## <a name="next-steps"></a>次の手順

+ [SQL Server の machine learning のチュートリアル](machine-learning-services-tutorials.md)




