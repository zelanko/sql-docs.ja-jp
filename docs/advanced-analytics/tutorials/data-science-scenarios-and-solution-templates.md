---
title: データ サイエンスのシナリオとソリューション テンプレート]、[SQL Server Machine Learning
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 1c98f6110aa6cc0bbb86f04a685211d7dc58447a
ms.sourcegitcommit: 671370ec2d49ed0159a418b9c9ac56acf43249ad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2019
ms.locfileid: "58072156"
---
# <a name="data-science-scenarios-and-solution-templates"></a>データ サイエンスのシナリオとソリューション テンプレート
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

テンプレートは、ソリューションを短時間で実装するために役立つベスト プラクティスを示し、構成要素を提供するサンプル ソリューションです。 各テンプレートは、特定の垂直方向または業界の特定の問題を解決するために設計されています。 各テンプレートのタスクは、データ準備や機能エンジニアリングから、モデルのトレーニングとスコアリングまで、多岐にわたります。 については、これらのテンプレートを使用してどのように[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]動作します。 次に、自由に独自のシナリオに合わせてカスタム ソリューションを構築するテンプレートをカスタマイズします。 

各ソリューションには、サンプル データ、R コード、または Python のコードが含まれていて、該当する場合、SQL ストアド プロシージャ。 コードは、SQL Server の計算の優先 R または Python 開発環境で実行できます。 場合によっては、T-SQL と SQL Server Management Studio など、任意の SQL クライアント ツールを使用して直接コードを実行できます。

> [!TIP]
> 
> テンプレートのほとんどは、オンプレミスでもサポートしている複数のバージョンので、機械学習のためのプラットフォームをクラウドします。 たとえば、SQL サーバーのみを使用してソリューションをビルドすることができます。 または Microsoft R Server、または Azure Machine Learning ソリューションをビルドすることができます。

+ 詳細と更新プログラムは、このお知らせを参照してください。[Azure ML の魅力的な新しいテンプレート](https://blogs.technet.microsoft.com/machinelearning/2015/04/09/exciting-new-templates-in-azure-ml/)

+ ダウンロードとセットアップ手順については、次を参照してください。[テンプレートを使用する方法](#bkmk_HowTo)します。

## <a name="fraud-detection"></a>不正行為の検出

[オンライン不正行為検出テンプレート (SQL Server R Services)](https://github.com/Microsoft/r-server-fraud-detection)

**内容。** 不正なトランザクションを検出する機能は、オンライン ビジネスにとって重要です。 チャージ バックの損失を減らすためには、企業が盗難された支払用の道具や資格情報を使用して行われた取引をすばやく特定する必要があります。 不正な取引が検出された場合、通常、それ以上の損失を防ぐために、できるだけ早く特定のアカウントをブロックする措置を取ります。 このシナリオでは、オンライン購入トランザクションからデータを使用して、不正行為の可能性を特定する方法について説明します。

**方法:** 不正行為の検出は、二項分類問題として解決されます。 このテンプレートに使用する手法は、他のドメインの不正行為の検出にも簡単に適用できます。


## <a name="campaign-optimization"></a>キャンペーンの最適化

[方法とタイミングを予測する潜在顧客に連絡するには](https://microsoft.github.io/r-server-campaign-optimization/)

**内容。** このソリューションでは、人口統計、履歴応答データ、および製品に固有の詳細に基づいて潜在顧客を予測するのに保険業界のデータを使用します。  推奨事項は、最適なチャネルと購入行動に影響を与える方法ユーザーまでの時間を示すも生成されます。

**方法:** ソリューションでは、作成し、複数のモデルを比較します。 ソリューションは、自動化されたデータ統合およびストアド プロシージャを使用してデータの準備にも示しています。 SQL Server データベース内、Azure HDInsight Spark での並列のサンプルが提供されます。 

## <a name="health-care-predict-length-of-stay-in-hospital"></a>医療: 病院入院の予測 

[入院期間の長さを予測します。](https://gallery.cortanaintelligence.com/Solution/Predicting-Length-of-Stay-in-Hospitals-1)

**内容。** 医療と計画の重要な部分は、正確に予測する患者は長期入院必要があります。 管理者は、施設に必要なその他のリソースを決定する必要があるし、医療従事者ができる、患者のニーズを満たしていることを保証します。

**方法:** このソリューションは、データ サイエンス仮想マシンを使用し、有効になっている machine learning での SQL Server のインスタンスが含まれています。 配置済みモデルとの対話に使用できる Power BI レポートのセットも含まれています。

## <a name="customer-churn"></a>顧客離れ

[顧客離れ予測テンプレート (SQL Server R Services)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/Churn/README.md)

**内容。** 分析と予測の顧客離れ、競合他社のお客様の損失を管理および防止する必要があります業界で重要: 銀行、電気通信、および量販店、いくつかの名前。 顧客離れ分析の目標は、離れる可能性が高い顧客を特定し、そのような顧客が離れないようにして、ビジネスを維持することです。

**方法:** このテンプレートの作成、顧客離れの問題として、**二項分類**問題。 顧客層と顧客トランザクションという 2 つのソースからサンプル データを使用し、顧客離れを起こす可能性が高い顧客と低い顧客を分類します。
  
## <a name="predictive-maintenance"></a>予測メンテナンス

[予測メンテナンス テンプレート (SQL Server 2016)](https://github.com/Microsoft/SQL-Server-R-Services-Samples/blob/master/PredictiveMaintenance/README.md)

**内容。** 予測的なメンテナンスでは、過去のエラーをキャプチャしてその情報を使用して、デバイスが失敗するタイミングと場所を予測するメンテナンス タスクの効率を向上させる目的としています。 デバイスの陳腐化を予測する機能は、分散データやセンサーに依存するアプリケーションに対して特に有効です。 このメソッドは、監視または IoT (モ ノのインターネット) デバイスでエラーを予測にも適用可能性があります。

詳細については、このお知らせを参照してください。[新しい予測メンテナンス テンプレート](https://blogs.technet.microsoft.com/machinelearning/2015/04/09/exciting-new-templates-in-azure-ml/)

**方法:** このソリューションは、「は現在のマシンが失敗した場合ですか?」という質問の答えに重点を置いています 入力データは、航空機のエンジン用にシミュレートされているセンサーの測定値を示します。 現在の動作サイクル、設定、およびセンサーの測定値などのエンジンの現在の操作状態を監視から取得したデータを使用して、3 種類の予測モデルを作成します。

-   **回帰モデル**: エンジンにエラーが発生するまでの時間を予測します。 サンプル モデルでは、「残存耐用年数」(RUL)、「時間に失敗しました」(TTF) とも呼ばれるメトリックを予測します。
  
-   **分類モデル**: エンジンのエラーが発生する確率が高いかどうかを予測します。
  
    **二項分類モデル**予測のかどうか、エンジンは、一定期間内で失敗します。

    **多クラス分類モデル**予測の特定のエンジン失敗する可能性がある障害の可能性が高い期間を提供します。 たとえば、特定の日について、指定した日、または指定した日から何日後に任意のデバイスでエラーが発生する可能性が高いかどうかを予測できます。

## <a name="energy-demand-forecasting"></a>エネルギー需要予測

[エネルギー需要予測と SQL Server R Services のテンプレート](https://gallery.cortanaintelligence.com/Tutorial/Energy-Demand-Forecast-Template-with-SQL-Server-R-Services-1)

**内容:**:需要予測は、エネルギー、製品、サービスなどのさまざまな分野で重要な問題です。 正確な需要予測と、計画、リソースの割り当てより優れた運用を実施し、その他の重要なビジネスの意思の企業が役立ちます。 エネルギー分野での需要予測はエネルギーのストレージ コストを削減し、需要と供給を分散重要です。

**方法:** このテンプレートでは、SQL Server R Services を使用して電力需要を予測します。 予測に使用するモデルは、ランダム フォレスト回帰モデルに基づく**rxDForest**高性能な機械学習アルゴリズムの Microsoft R Server に含まれています。 このソリューションには、需要シミュレーター、モデルのトレーニングに必要なすべての R コードと T-SQL コード、予測の生成とレポートに使用できるストアド プロシージャが含まれています。 


## <a name="bkmk_HowTo"></a>テンプレートを使用する方法

各テンプレートに含まれるファイルをダウンロードするには、GitHub コマンドを使用するか、リンクを開いて **[Download Zip (Zip ファイルをダウンロード)]** をクリックし、すべてのファイルをコンピューターに保存します。  通常、ダウンロードしたソリューションには次のフォルダーが含まれています。
  
-   **データ**:アプリケーションごとにサンプル データが含まれています。
  
-   **R**:ソリューションに、必要なすべての R 開発コードが含まれています。 このソリューションには、Microsoft R Server に含まれるライブラリが必要ですが、任意の R IDE で開き、編集することができます。 この R コードは、SQL Server インスタンスに対する計算コンテキストを設定し、計算が "データベース内で" 実行されるように最適化されています。
  
-   **SQLR**:など、SQL 環境で実行できる複数の .sql ファイルが含まれています[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]データ処理などの関連タスクを実行するストアド プロシージャを作成するには、特徴エンジニア リング、およびモデルの展開。
  
    このフォルダーには、すべてのスクリプトを呼び出し、包括的な環境を作成できる PowerShell スクリプトも含まれています。 スクリプトは、必ず実際の環境似合わせて編集してください。

## <a name="next-steps"></a>次のステップ

+ [SQL Server machine learning のチュートリアル](machine-learning-services-tutorials.md)




