---
title: WideWorldImportersDW - ETL ワークフロー |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: sql
ms.technology: samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 36638c4cc2bda58ac277822d5c4a4ce5421ab8b4
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="wideworldimportersdw-etl-workflow"></a>WideWorldImportersDW ETL ワークフロー
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
使用して、 *WWI_Integration* ETL パッケージ データの変化に応じて、WideWorldImportersDW データベースに、WideWorldImporters データベースからデータを移行します。 パッケージを定期的に実行 (通常は毎日) です。

パッケージは、(Integration Services 内の別の変換) ではなく一括 T-SQL 操作を調整するため SQL Server Integration Services を使用して、高パフォーマンスを保証します。

ディメンションが最初に、読み込まれていて、ファクト テーブルが読み込まれます。 パッケージは、障害の後にいつでも実行できます。

ワークフローは、次のようになります。

 ![WideWorldImporters ETL ワークフロー](media/wide-world-importers/wideworldimporters-etl-workflow.png)

ワークフローは、適切な終了時刻を決定する式タスクを開始します。 終了時刻は、数分-現在の時刻です。 (このアプローチは、現在の時刻に直接データを要求するよりも堅牢です)。任意のミリ秒単位は、時間から切り詰められます。

日付ディメンション テーブルを設定することで、メイン処理を開始します。 処理により、テーブルの現在の年のすべての日付が入力されていること。

次に、一連のデータ フロー タスクは、各ディメンションを読み込みます。 次に、各ファクトを読み込まれるとします。

## <a name="prerequisites"></a>前提条件

- SQL Server 2016 (またはそれ以降)、データベースとの WideWorldImporters と WideWorldImportersDW (同じまたは異なる SQL Server のインスタンスで)
- SQL Server Management Studio
- SQL Server 2016 Integration Services
  - Integration Services カタログを作成することを確認します。 SQL Server Management Studio オブジェクト エクスプ ローラーで、Integration Services カタログを作成するには、右**Integration Services**、し、**カタログの追加**です。 既定のオプションのままにします。 SQLCLR を有効にし、パスワードの入力を求められます。


## <a name="download"></a>ダウンロード

サンプルの最新のリリースでは、次を参照してください。 [wide world importers 社リリース](http://go.microsoft.com/fwlink/?LinkID=800630)です。 ダウンロード、*毎日 ETL.ispac* Integration Services パッケージのファイルです。

ソース コード、サンプル データベースを再作成を次を参照してください。 [wide world-importers 社](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-integration-etl)です。

## <a name="install"></a>インストール

1. Integration Services パッケージを展開します。
   1. Windows エクスプ ローラーで開く、*毎日 ETL.ispac*パッケージです。 これは、SQL Server Integration Services 配置ウィザードを起動します。
   2. **ソースの選択**、プロジェクトの配置の既定値の後ろを指すパスと、*毎日 ETL.ispac*パッケージです。
   3. **先の選択**、Integration Services カタログをホストするサーバーの名前を入力します。
   4. という名前の新しいフォルダーに、たとえば、Integration Services カタログの下のパスを選択*WideWorldImporters*です。
   5. 選択**展開**ウィザードを終了します。

2. ETL プロセスの SQL Server エージェント ジョブを作成します。
   1. Management Studio を右クリックして**SQL Server エージェント**、し、**新規** > **ジョブ**です。
   2. たとえば、名前を入力*WideWorldImporters ETL*です。
   3. 追加、**ジョブ ステップ**型の**SQL Server Integration Services パッケージ**です。
   4. Integration Services カタログをあるサーバーを選択し、、*毎日 ETL*パッケージです。
   5. **構成** > **接続マネージャー**ソースとターゲットへの接続が正しく構成されていることを確認してください。 既定では、ローカル インスタンスに接続します。
   6. 選択**OK**ジョブを作成します。

3. 実行またはジョブ スケジュールを設定します。
