---
title: ワイドワールドインポーターズDW - ETLワークフロー |マイクロソフトドキュメント
description: Sql Server 統合サービス (SSIS) を含む ETL パッケージを使用して、WideWorldImporters データベースから WideWorldImportersDW に定期的にデータを移行します。
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 98ce2b9aa11b2e1381da1f16455df8a2c0d3f243
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81487431"
---
# <a name="wideworldimportersdw-etl-workflow"></a>ETL ワークフロー
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
*WWI_Integration* ETL パッケージを使用して、データの変更に応じて、WideWorldImporters データベースから WideWorldImportersDW データベースにデータを移行します。 パッケージは定期的に (通常は毎日) 実行されます。

このパッケージは、SQL Server 統合サービスを使用して (統合サービスで個別の変換ではなく) 一括 T-SQL 操作を調整することで、高いパフォーマンスを保証します。

ディメンションが最初に読み込まれ、次にファクト テーブルが読み込まれます。 障害発生後はいつでもパッケージを再実行できます。

ワークフローは次のようになります。

 ![ワイドワールドインポーターETLワークフロー](media/wide-world-importers/wideworldimporters-etl-workflow.png)

ワークフローは、適切なカットオフ時間を決定する式タスクから開始されます。 カットオフ時間は現在の時刻から数分を引いた値です。 (この方法は、現在の時刻にデータを要求するよりも堅牢です)。ミリ秒は、その時点から切り捨てられます。

メイン処理は、Date ディメンション テーブルにデータを設定することで開始します。 この処理により、現在の年のすべての日付がテーブルに確実に入力されます。

次に、一連のデータ フロー タスクが各ディメンションを読み込みます。 次に、各ファクトを読み込みます。

## <a name="prerequisites"></a>前提条件

- SQL Server 2016 以降、ワイドワールド インポートとワイドワールド インポートデータDW データベース (SQL Server の同じインスタンスまたは異なるインスタンス内)
- SQL Server Management Studio
- SQL Server 2016 Integration Services
  - 必ず統合サービス カタログを作成してください。 統合サービス カタログを作成するには、 SQL Server 管理スタジオ オブジェクト エクスプローラーで [**統合サービス**] を右クリックし、 **[ カタログの追加**] をクリックします。 デフォルトのオプションはそのままにします。 SQLCLR を有効にしてパスワードを入力するように求められます。


## <a name="download"></a>ダウンロード

サンプルの最新リリースについては、[全世界の輸入業者リリース](https://go.microsoft.com/fwlink/?LinkID=800630)を参照してください。 *毎日の ETL.ispac*統合サービス パッケージ ファイルをダウンロードします。

サンプル データベースを再作成するソース コードについては、「[全世界のインポーター](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-ssis)」を参照してください。

## <a name="install"></a>インストール

1. 統合サービス パッケージを展開します。
   1. エクスプローラで、*毎日 ETL.ispac*パッケージを開きます。 SQL Server 統合サービス展開ウィザードが起動します。
   2. [**ソースの選択**] で、[プロジェクトの展開] のデフォルトに従い、*毎日の ETL.ispac*パッケージを指すパスを使用します。
   3. [**宛先の選択**] に、統合サービス カタログをホストするサーバーの名前を入力します。
   4. 統合サービス カタログの下のパスを*選択します。*
   5. [**展開]** を選択してウィザードを終了します。

2. ETL プロセス用の SQL Server エージェント ジョブを作成します。
   1. 管理スタジオで、[ SQL **Server エージェント**] を右クリックし、 **[ 新しい** > **ジョブ**] をクリックします。
   2. 名前を*入力します。*
   3. **SQL Server 統合サービス パッケージ**の種類のジョブ**ステップ**を追加します。
   4. 統合サービス カタログを持つサーバーを選択し、*日次 ETL*パッケージを選択します。
   5. [**構成** > **接続マネージャ**] で、ソースとターゲットへの接続が正しく構成されていることを確認します。 デフォルトでは、ローカル インスタンスに接続します。
   6. **[OK] を**選択してジョブを作成します。

3. ジョブを実行またはスケジュールします。
