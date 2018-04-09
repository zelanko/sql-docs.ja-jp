---
title: WideWorldImportersDW - ETL ワークフロー |Microsoft ドキュメント
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: ''
ms.component: samples
ms.technology:
- samples
ms.custom: ''
ms.date: 04/04/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: article
author: BarbKess
ms.author: barbkess
manager: craigg
robots: noindex,nofollow
ms.workload: Inactive
ms.openlocfilehash: 5b475ee3299431327237efdeee723a88dd832784
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2018
---
# <a name="wideworldimportersdw-etl-workflow"></a>WideWorldImportersDW ETL workflow
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
WWI_Integration ETL パッケージを使用して、データの変化に応じて WideWorldImportersDW データベースへの WideWorldImporters データベースからデータを移行します。 パッケージを定期的に実行 (最もよく毎日) です。

## <a name="overview"></a>概要

パッケージに使用されている一括 T-SQL 操作を調整するため SQL Server Integration Services (SSIS) (としてではなく SSIS 内の別の変換) のデザインを高パフォーマンスを確認します。

ディメンションは、ファクト テーブルによってその後に最初に読み込まれます。 パッケージは、障害の後にいつでも再実行できます。

ワークフローは次のとおりです。

 ![WideWorldImporters ETL ワークフロー](media/wide-world-importers/wideworldimporters-etl-workflow.png)

これは、適切な終了時刻を動作する式タスクを開始します。 この時間は、小さい数分の現在の時刻です。 (これは現在の時刻に直接データを要求するよりも堅牢) です。 時間 (ミリ秒) の切り捨てられます。

日付ディメンション テーブルを設定することで、メイン処理を開始します。 テーブルの現在の年のすべての日付が入力されていることを保証します。

その後は、一連のデータ フロー タスクは、各ディメンションし、各ファクトを読み込みます。

## <a name="prerequisites"></a>前提条件

- SQL Server 2016 (またはそれ以降)、データベースとの WideWorldImporters と WideWorldImportersDW です。 これらは、SQL Server の同じまたは別のインスタンスに配置できます。
- SQL Server Management Studio (SSMS)
- SQL Server 2016 Integration Services (SSIS)。
  - SSIS カタログを作成したことを確認してください。 いない場合は、右クリック**Integration Services** SSMS オブジェクト エクスプ ローラーで選択および**カタログの追加**です。 既定の設定に従います。 Sqlclr を有効にし、パスワードを指定することを依頼します。


## <a name="download"></a>ダウンロード

サンプルの最新リリース。

[wide-world-importers-release](http://go.microsoft.com/fwlink/?LinkID=800630)

SSIS パッケージ ファイルをダウンロード**毎日 ETL.ispac**です。

サンプル データベースを再作成するソース コードは、次の場所から使用可能なです。

[wide-world-importers](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/wide-world-importers/wwi-integration-etl)

## <a name="install"></a>インストール

1. SSIS パッケージを展開します。
   - Windows エクスプ ローラーから、"日次 ETL.ispac"パッケージを開きます。 これにより、Integration Services 配置ウィザードが起動します。
   - [ソースの選択] の下にある"毎日 ETL.ispac"パッケージを指すパスで既定のプロジェクトの配置に準拠します。
   - 「先」の下には、SSIS カタログをホストするサーバーの名前を入力します。
   - 新しいフォルダー"WideWorldImporters"下にあるなど、SSIS カタログの下のパスを選択します。
   - [配置] をクリックしてウィザードを完了します。

2. ETL プロセスの SQL Server エージェント ジョブを作成します。
   - SSMS では、右クリックして「SQL Server エージェント」と 新規-> ジョブ
   - 名前をたとえば"WideWorldImporters ETL"を選択します。
   - 「SQL Server Integration Services パッケージ」の種類のジョブ ステップを追加します。
   - SSIS カタログを使用してサーバーを選択し、"毎日"の ETL パッケージを選択します。
   - 構成-> 接続マネージャーは、ソースとターゲットへの接続が正しく構成されていることを確認します。 既定では、ローカル インスタンスに接続します。
   - ジョブを作成するには、[ok] をクリックします。

3. 実行またはジョブ スケジュールを設定します。
