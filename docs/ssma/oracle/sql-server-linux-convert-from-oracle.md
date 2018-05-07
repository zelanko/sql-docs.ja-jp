---
title: Linux 上の SQL Server への Oracle HR スキーマの移行 |Microsoft ドキュメント
description: Oracle スキーマのサンプルを SQL Server on Linux に変換します。
author: edmacauley
ms.author: edmacauley
manager: craigg
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssma-oracle
ms.suite: sql
ms.custom: ''
ms.technology: database-engine
ms.openlocfilehash: b044f54f172bc354c9c0a14e6628678911dbb82c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="migrate-an-oracle-schema-to-sql-server-2017-on-linux-with-the-sql-server-migration-assistant"></a>SQL Server Migration Assistant Linux での SQL Server 2017 への Oracle スキーマを移行します。

このチュートリアルを使用して SQL Server Migration Assistant (SSMA) for Windows 上の Oracle 変換 Oracle サンプル**HR**スキーマ[Linux 上の SQL Server 2017](../../linux/sql-server-linux-overview.md)です。

> [!div class="checklist"]
> * ダウンロードしてインストール SSMA Windows
> * 移行を管理する SSMA プロジェクトを作成します。
> * Oracle への接続
> * 移行レポートを実行します。
> * サンプルの人事部のスキーマを変換します。
> * データを移行します。

## <a name="prerequisites"></a>前提条件

- Oracle 12c の (12.2.0.1.0) を持つインスタンス、 **HR**スキーマがインストールされています。
- Linux 上の SQL Server の作業インスタンス

> [!NOTE]
> 同じ手順を使用すると、Windows では、SQL Server を対象で Windows を選択する必要があります、**移行先**プロジェクトの設定。

## <a name="download-and-install-ssma-for-oracle"></a>ダウンロードして SSMA for Oracle をインストール

SQL Server Migration Assistant のいくつかのエディションは、ソース データベースによって、使用できます。  現在のバージョンをダウンロード[SQL Server Migration Assistant for Oracle](http://aka.ms/ssmafororacle)し、ダウンロード ページにある命令を使用してインストールします。

> [!NOTE]
> この時点で、 **SSMA for Oracle の拡張機能パック**は Linux では、サポートされていませんが、このチュートリアルの必要はありません。

## <a name="create-and-set-up-project"></a>作成し、セットアップ プロジェクト

新しい SSMA プロジェクトを作成するのにには、次の手順を使用します。

1. SSMA for Oracle を開き、**新しいプロジェクト**から、**ファイル**メニュー。

1. プロジェクトの名前を付けます。

1. "SQL Server 2017 (Linux) - プレビュー"を選択して、**移行先**フィールドです。

SSMA for Oracle は Oracle サンプル スキーマが既定では使用されません。 人事部のスキーマを有効にするには、次の手順を使用します。

1. SSMA、選択、**ツール**メニュー。

1. 選択**プロジェクト設定の既定の**を選択し**システム オブジェクトの読み込み**です。

1. 確認**HR**が確認され、選択**OK**。

## <a name="connect-to-oracle"></a>Oracle への接続

次に、SSMA を Oracle に接続します。

1. ツールバーで、をクリックして**Connect to Oracle**です。

1. サーバー名、ポート、Oracle SID、ユーザー名およびパスワードを入力します。

   ![Oracle への接続](./media/sql-server-linux-convert-from-oracle/ConnectToOracle.png)

1. 続いて、 **[接続]** をクリックします。 しばらく後は、SSMA for Oracle は、データベースに接続し、そのメタデータを読み取ります。

## <a name="create-a-report"></a>レポートを作成します。

次の手順を使用すると、移行レポートを生成できます。

1. **Oracle メタデータ エクスプ ローラー**サーバーのノードを展開します。

1. 展開**スキーマ**を右クリックして**HR**を選択して**レポートの作成**です。

   ![Oracle メタデータ エクスプ ローラーは、レポートを作成します。](./media/sql-server-linux-convert-from-oracle/CreateReport.png)

1. すべての警告と、変換に関連するエラーの一覧を表示するレポートを新しいブラウザー ウィンドウが開きます。

   > [!NOTE]
   > このチュートリアルではそのリストに何もする必要はありません。 Oracle データベースの次の手順を実行する場合は、データベースのすべての重要な変換の問題に対処するレポートを確認してください。

   ![移行のサンプル レポート](./media/sql-server-linux-convert-from-oracle/SSMAReport.png)

## <a name="connect-to-sql-server"></a>SQL Server への接続

次に選択**SQL Server への接続**適切な接続情報を入力します。  存在データベース名がないを使用する場合は、SSMA for Oracle が自動的に作成します。

![SQL Server への接続](./media/sql-server-linux-convert-from-oracle/ConnectToSQLServer.png)

## <a name="convert-schema"></a>スキーマを変換します。

右クリックして**HR**で**Oracle メタデータ エクスプ ローラー**スキーマの変換を選択します。

![スキーマを変換します。](./media/sql-server-linux-convert-from-oracle/ConvertSchema.png)

## <a name="synchronize-database"></a>データベースを同期します。

次に、データベースを同期します。

1. 変換が完了したらを使用して、 **SQL Server メタデータ エクスプ ローラー**前の手順で作成したデータベースに移動します。

1. データベースを右クリックして**データベースと同期する**、[ok] をクリックします。

   ![データベースと同期します。](./media/sql-server-linux-convert-from-oracle/SynchronizeWithDatabase.png)

## <a name="migrate-data"></a>データを移行します。

最後に、データの移行を開始します。

1. **Oracle メタデータ エクスプ ローラー**を右クリックして**HR**を選択して**データの移行**です。

1. データ移行の手順では、Oracle と SQL Server 資格情報を再入力することが必要です。

1. 完了したら、次のスクリーン ショットのようになりますデータ移行レポートを確認します。

   ![データ移行レポート](./media/sql-server-linux-convert-from-oracle/DataMigrationReport.png)

## <a name="next-steps"></a>次の手順

複雑な Orcale スキーマの変換処理が行われます。 複数の時刻、テスト、およびクライアント アプリケーションが変更される可能性です。 このチュートリアルの目的では、全体的な移行プロセスの一部として Oracle の SSMA を使用する方法を説明します。

このチュートリアルで学習した方法。
> [!div class="checklist"]
> * SSMA Windows 上にインストールします。
> * 新しい SSMA プロジェクトを作成します。
> * 評価し、Oracle からの移行を実行

SSMA を使用する他の方法を次に、探索するには。

> [!div class="nextstepaction"]
>[SQL Server Migration Assistant のドキュメント](../sql-server-migration-assistant.md)
