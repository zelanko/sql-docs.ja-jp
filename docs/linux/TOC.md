# [SQL Server on Linux について](sql-server-linux-overview.md)

# 概要
## [リリース ノート](sql-server-linux-release-notes.md)
## [このリリースの新機能](sql-server-linux-whats-new.md)
## [新規および最近の更新記事](new-updated-linux.md)
## [エディションとサポートされる機能](sql-server-linux-editions-and-components-2017.md)

# クイック スタート
## [インストールと接続 - Red Hat](quickstart-install-connect-red-hat.md)
## [インストールと接続 - SUSE](quickstart-install-connect-suse.md)
## [インストールと接続 - Ubuntu](quickstart-install-connect-ubuntu.md)
## [実行と接続 - Docker](quickstart-install-connect-docker.md)
## [Azure での SQL VM プロビジョニング](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

# チュートリアル
## [1_Windows からの移行](sql-server-linux-migrate-restore-database.md)
## [2_Oracle からの移行](../ssma/oracle/sql-server-linux-convert-from-oracle.md?toc=%2fsql%2flinux%2ftoc.json)
## [3_Docker への移行](tutorial-restore-backup-in-sql-server-container.md)
## [4_ジョブの作成](sql-server-linux-run-sql-server-agent-job.md)
## [5_AD 認証のセットアップ](sql-server-linux-active-directory-authentication.md)
## [6_フェールオーバー クラスター インスタンスの作成](sql-server-linux-shared-disk-cluster-configure.md)
### [iSCSI](sql-server-linux-shared-disk-cluster-configure-iscsi.md)
### [NFS](sql-server-linux-shared-disk-cluster-configure-nfs.md)
### [SMB](sql-server-linux-shared-disk-cluster-configure-smb.md)

# 概念
## Install
### [SQL Server のインストール](sql-server-linux-setup.md)
### [SQL Server ツールのインストール](sql-server-linux-setup-tools.md)
### [SQL Server エージェントのインストール](sql-server-linux-setup-sql-agent.md)
### [SQL Server フルテキスト検索のインストール](sql-server-linux-setup-full-text-search.md)
### [SQL Server Integration Services のインストール](sql-server-linux-setup-ssis.md)
### [GA リポジトリの登録](sql-server-linux-change-repo.md)

## [構成]
### [mssql-conf での構成](sql-server-linux-configure-mssql-conf.md)
### [環境変数](sql-server-linux-configure-environment-variables.md)
### [Docker コンテナーの構成](sql-server-linux-configure-docker.md)
### [カスタマー フィードバック](sql-server-linux-customer-feedback.md)

## [開発](sql-server-linux-develop-overview.md)
### [接続ライブラリ](sql-server-linux-develop-connectivity-libraries.md)
### [Visual Studio Code の使用](sql-server-linux-develop-use-vscode.md)
### [SSMS の使用](sql-server-linux-develop-use-ssms.md)
### [SSDT の使用](sql-server-linux-develop-use-ssdt.md)

## [管理](sql-server-linux-management-overview.md)
### [SSMS を使用した管理](sql-server-linux-manage-ssms.md)
### [PowerShell を使用した管理](sql-server-linux-manage-powershell.md)
### [ログ配布の使用](sql-server-linux-use-log-shipping.md)
### [データベース メールと電子メール アラートの使用](sql-server-linux-db-mail-sql-agent.md)

## [移行](sql-server-linux-migrate-overview.md)
### [Windows から BACPAC のエクスポートとインポート](sql-server-linux-migrate-ssms.md)
### [SQL Server Migration Assistant を使用した移行](sql-server-linux-migrate-ssma.md)
### [bcp を使用した一括コピー](sql-server-linux-migrate-bcp.md)

## [抽出、変換、読み込み](sql-server-linux-migrate-ssis.md)
### [SSIS の構成](sql-server-linux-configure-ssis.md)
### [SSIS パッケージのスケジュール設定](sql-server-linux-schedule-ssis-packages.md)

## [ビジネス継続性の構成](sql-server-linux-business-continuity-dr.md)
### [バックアップと復元](sql-server-linux-backup-and-restore-database.md)
#### [仮想デバイス インターフェイス - Linux](sql-server-linux-backup-vdi-specification.md)
### [フェールオーバー クラスター インスタンス](sql-server-linux-shared-disk-cluster-concepts.md)
#### [Red Hat Enterprise Linux]()
##### [構成 (HA アドオン)](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)
##### [操作 (HA アドオン)](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
#### [SUSE Linux Enterprise Server]()
##### [構成 (HA アドオン)](sql-server-linux-shared-disk-cluster-sles-configure.md)
### [可用性グループ](sql-server-linux-availability-group-overview.md)
#### [高可用性のための作成](sql-server-linux-availability-group-ha.md)
##### [AG の構成](sql-server-linux-availability-group-configure-ha.md)
##### [RHEL での構成](sql-server-linux-availability-group-cluster-rhel.md)
##### [SUSE での構成](sql-server-linux-availability-group-cluster-sles.md)
##### [Ubuntu での構成](sql-server-linux-availability-group-cluster-ubuntu.md)
##### [操作](sql-server-linux-availability-group-failover-ha.md)
#### [スケール アウトのみを読み取るために作成]()
##### [AG の構成](sql-server-linux-availability-group-configure-rs.md)

## [セキュリティ](sql-server-linux-security-overview.md)
### [セキュリティ機能の入門](sql-server-linux-security-get-started.md)
### [接続の暗号化](sql-server-linux-encrypted-connections.md)

## パフォーマンス
### [ベスト プラクティス](sql-server-linux-performance-best-practices.md)
### [パフォーマンス機能の概要](sql-server-linux-performance-get-started.md)

# サンプル
## 無人インストール
### [Red Hat Enterprise Linux](sample-unattended-install-redhat.md)
### [SUSE Linux Enterprise Server](sample-unattended-install-suse.md)
### [Ubuntu](sample-unattended-install-ubuntu.md)

# リソース
## [[トラブルシューティング]](sql-server-linux-troubleshooting-guide.md)
## [SQL Server のドキュメント](../sql-server/sql-server-technical-documentation.md)
## パートナー
### [監視](../sql-server/partner-monitor-sql-server.md)
### [高可用性とディザスター リカバリー](../sql-server/partner-hadr-sql-server.md)
### [管理](../sql-server/partner-management-sql-server.md)
### [開発](../sql-server/partner-dev-sql-server.md)
## [DBA Stack Exchange](https://dba.stackexchange.com/questions/tagged/sql-server)
## [Stack Overflow](http://stackoverflow.com/questions/tagged/sql-server)
## [MSDN フォーラム](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
## [Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback)
## [Reddit](https://www.reddit.com/r/SQLServer)
