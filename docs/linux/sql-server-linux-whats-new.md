---
title: "Linux 上の SQL Server 2017 RC1 の新機能 |Microsoft ドキュメント"
description: "このトピックでは、Linux 上の SQL Server 2017 の現在のリリースの新機能が強調表示されます。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 08/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 456b6f31-6b97-4e31-80ab-b40151ec4868
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 649c7cbd03b6d2e61dbbb572a34cdbcd2a7ab7cd
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="whats-new-for-sql-server-2017-on-linux"></a>Linux 上の SQL Server 2017 の新機能します。

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このトピックでは、Linux で実行されている SQL Server 2017 の新機能について説明します。

## <a name="rc2"></a>RC2

RC2 リリースには、その他のバグ修正と機能強化が含まれています。

## <a name="rc1"></a>RC1

RC1 リリースには、次の機能強化と修正が含まれています。

- 暗号化された接続の透過的な層セキュリティ (TLS) を有効になります。 詳細については、次を参照してください。 [Linux に SQL Server への接続の暗号化](sql-server-linux-encrypted-connections.md)です。
- 有効になっている[Active Directory 認証](sql-server-linux-active-directory-authentication.md)です。
- 有効になっている[DB メール](../relational-databases/database-mail/database-mail.md)です。
- IPV6 サポートを追加します。
- 最初の SQL Server セットアップの追加の環境変数です。 詳細については、次を参照してください。 [Linux 上の環境変数と SQL Server の構成設定](sql-server-linux-configure-environment-variables.md)です。
- 削除**sqlpackage**からバイナリをインストールします。 SqlPackage 実行できます Linux に対してリモートで Windows からです。
- ようなリソース名では、Windows SQL Server フェールオーバー クラスター インスタンスでディスク クラスター リソース エージェントのセットを共有します。 `@@ServerName`SQL Server の共有ディスク クラスター リソース名以外を返しますRC1 より前は、リソースを所有しているクラスター ノードの名前が返されます。

## <a name="ctp-21"></a>CTP 2.1

CTP 2.1 リリースには、次の機能強化と修正が含まれています。

- 追加[SQL Server サービスを構成する環境変数](sql-server-linux-configure-environment-variables.md)です。
- [mssql conf](sql-server-linux-configure-mssql-conf.md)今すぐ設定の 2 部構成の名前付け規則が必要です。
- [Mssql scripter](https://github.com/Microsoft/sql-xplat-cli)ツールです。 このユーティリティを使用を生成するには、開発者、Dba、およびシステム管理者`CREATE`と`INSERT`コマンドラインからの SQL Server、Azure SQL DB、および Azure SQL DW データベース内のデータベース オブジェクトからの TRANSACT-SQL スクリプト。
- [DBFS ツール](https://github.com/Microsoft/dbfs)です。 これは、Linux オペレーティング システムで、仮想ディレクトリでの仮想ファイルとして Dba とシステム管理者は、SQL Server 動的管理ビュー (Dmv) からのライブ データを公開することで、SQL Server をより簡単に監視を有効にするオープン ソース ツールです。
- SQL Server Integration Services (SSIS) は、Linux で実行されます。 さらに、コマンドラインから Linux 上の SSIS パッケージを実行できるようにする新しいパッケージがあります。 詳細については、次を参照してください。、 [Linux の SSIS サポート ブログの投稿 announcing](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)です。 Linux CTP 2.1 の更新で、SSIS で SSIS パッケージは、Linux の ODBC 接続を使用できます。 詳細については、次を参照してください。、 [Linux 上のブログの投稿 announcing ODBC サポート](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)です。

## <a name="ctp-20"></a>(CTP 2.0)

CTP 2.0 リリースには、次の機能強化と修正が含まれています。

- 追加**ログ配布**SQL Server エージェントの機能です。
- Mssql 構成のローカライズされたメッセージ
- Linux のパスの書式設定は、SQL Server エンジン全体にわたって互換性がようになりました。 サポートが、"c:\\"プレフィックスが指定されたパスが続行されます。
- DMV を有効になっている**sys.dm_os_file_exists**です。
- DMV を有効になっている**sys.fn_trace_gettable**です。
- 追加[CLR 厳格なセキュリティ モード](/sql/database-engine/configure-windows/clr-strict-security)です。
- SQL のグラフ。
- 再開可能なオンライン インデックス再構築します。
- アダプティブ クエリ処理します。
- Utf-8 エンコード ログ ファイルなど、システム ファイルを追加します。
- インメモリ データベースの場所の制限を固定します。 
- 新しいクラスターの種類の追加`CLUSTER_TYPE = EXTERNAL`の高可用性の可用性グループを構成します。
- 読み取り専用ルーティングの可用性グループ リスナーを修正します。
- 早期導入プログラム (EAP) の顧客の運用環境がサポートされます。 サインアップ[ここ](http://aka.ms/eapsignup)です。

## <a name="ctp-14"></a>CTP 1.4

CTP 1.4 のリリースには、次の機能強化と修正が含まれています。

- 有効になっている、 [SQL Server エージェント](sql-server-linux-setup-sql-agent.md)です。
  - T-SQL のジョブ機能を有効になります。
- 固定タイム ゾーンのバグ:
  - アジア/コルカタのタイム ゾーンをサポートします。
  - 固定 GETDATE() 関数。
- 非同期のネットワークは/0 の機能強化。
  - インメモリ OLTP ワークロードのパフォーマンスを大幅に向上します。
- Docker のイメージには、SQL Server コマンド ライン ユーティリティが含まれています。 (sqlcmd と bcp)。
- バックアップ Virtual Device Interface (VDI) のサポートを有効になります。
- 使用してインストールした後は TempDB の場所を編集できるよう`ALTER DATABASE`です。

## <a name="ctp-13"></a>CTP 1.3

1.3 の CTP リリースには、次の機能強化と修正が含まれています。

- 有効になっている[フル テキスト検索](sql-server-linux-setup-full-text-search.md)機能します。
- 常に有効になっている[可用性グループ機能](sql-server-linux-availability-group-overview.md)高可用性を実現します。
- 追加の機能**mssql conf**:
  - 最初にセットアップを使用して**mssql conf**です。 Mssql-conf での使用を参照してください、[環境向けインストール ガイド](sql-server-linux-setup.md#platforms)です。
  - 可用性グループを有効にします。 参照してください、[可用性グループ トピック](sql-server-linux-availability-group-overview.md)です。
- 固定のネイティブの Linux パスは、インメモリ OLTP ファイル グループのサポートします。
- Dm_os_host_info DMV の機能を有効になります。

## <a name="ctp-12"></a>CTP 1.2

1.2 の CTP リリースには、次の機能強化と修正が含まれています。

- サポート[SUSE Linux Enterprise Server v12 SP2](quickstart-install-connect-suse.md)です。
- コア エンジンと安定性の向上のためのバグ修正。
- Docker の画像: 
  - 固定[1 を発行](https://github.com/Microsoft/mssql-docker/issues/1)Python をイメージに追加しています。
  - 削除`/opt/mssql/data`既定ボリュームとして。
- .NET 4.6.2 に更新されます。

## <a name="ctp-11"></a>CTP 1.1

CTP 1.1 リリースには、次の機能強化と修正が含まれています。

- Red Hat Enterprise Linux バージョン 7.3 をサポートします。
- Ubuntu 16.10 をサポートします。
- Ubuntu 16.04 に Docker OS のレイヤーをアップグレードします。
- Docker イメージで製品利用統計情報の問題を修正します。
- バグを修正した SQL Server セットアップ スクリプトに関連します。
- ネイティブ コンパイル T-SQL モジュールなどのパフォーマンスを向上します。
  - **OPENJSON**、 **FOR JSON**、 **JSON**組み込み要素。
  - 計算 (唯一のインデックスは許可されている列は計算列の非永続化ではなく保存される計算列で、インメモリ テーブルの)。
  - **CROSS APPLY**操作します。
- 新しい言語機能:
  - 文字列関数:**トリム**、 **CONCAT_WS**、**翻訳**と**STRING_AGG**サポート**WITHIN GROUP (ORDER BY)**です。
  - **一括インポート**CSV 形式とファイルのソースとしての Azure Blob ストレージがサポートされました。

互換性モード 140。

- 行がデルタ ストアの場合は、非クラスター化列ストア インデックスの場合に更新プログラムのパフォーマンスを向上します。 削除から変更操作と挿入を更新します。 またワイド文字列から絞り込むためのプランの形状を変更します。
- バッチ モードのクエリは、"memory grant フィードバック ループ"をサポートします。 これにより、同時実行とバッチ モードを使用する繰り返しのクエリを実行するシステムでスループットが向上します。 これにより、それ以外の場合、クエリを開始する前にメモリ ブロックしているシステムで実行するより多くのクエリが許可できます。
- バッチ モードでの単純なプランを無視することで、バッチ モードの並列処理のパフォーマンスの向上は、代わりに columnstore に対して選択される並列プランを許可する予定です。 

[Service Pack 1 からの機能強化](https://blogs.msdn.microsoft.com/sqlreleaseservices/sql-server-2016-service-pack-1-sp1-released/)CTP1.1 このリリースでは。
- 複製は、CLR、Filestream または Filetable、メモリ内とクエリ ストア オブジェクトのデータベースです。
- **作成**または**ALTER**プログラミング オブジェクトの演算子。
- 新しい**USE ヒント**クエリ ヒントを指定して、クエリ プロセッサのオプションです。 詳細:[クエリ ヒント](https://msdn.microsoft.com/en-us/library/ms181714.aspx)です。
- SQL サービス アカウント プログラムで識別できますページのロックを有効にするメモリおよびファイルの瞬時初期化のアクセス許可。
- TempDB ファイルの数、ファイルのサイズとファイル拡張設定をサポートします。
- Showplan XML での診断の拡張。
- 演算子ごとの軽量なクエリの実行プロファイルができます。
- 新しい動的管理関数**sys.dm_exec_query_statistics_xml**です。
- 増分統計の動的管理関数を新しいです。
- 削除されたノイズの多いメモリ内では、エラー ログからログ メッセージが関連します。
- AlwaysOn の待機時間の診断を向上します。
- 手動の変更の追跡をクリーンアップします。
- **DROP TABLE**レプリケーションをサポートします。
- **BULK INSERT**でヒープに**自動 TABLOCK** TF 715 下です。
- 並列**INSERT.選択**ローカル一時テーブルを変更します。

これらの修正プログラムの詳細について、 [Service Pack 1 リリース説明](https://blogs.msdn.microsoft.com/sqlreleaseservices/sql-server-2016-service-pack-1-sp1-released/)です。

多くのデータベース エンジンの機能強化は、Windows と Linux の両方に適用されます。 現在サポートされていない Linux でデータベース エンジン機能の唯一の例外になります。 詳細については、次を参照してください。 [SQL Server 2017 (データベース エンジン) の新](https://msdn.microsoft.com/library/mt775028)です。

## <a name="see-also"></a>参照

インストール要件、サポートされていない機能領域、および既知の問題を参照してください[Linux 上の SQL Server 2017 のリリース ノート](sql-server-linux-release-notes.md)です。

