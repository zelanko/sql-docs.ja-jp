---
title: 取得し、Parallel Data Warehouse のバックアップ サーバーの構成 |Microsoft Docs
description: この記事では、Analytics Platform System (APS) および並列データ ウェアハウス (PDW) のバックアップと復元機能で使用するためのバックアップ サーバーとして非アプライアンスの Windows システムを構成する方法について説明します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: f79cb13658328927cab81bbf8d559066c5a4d5cc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961644"
---
# <a name="acquire-and-configure-a-backup-server-for-parallel-data-warehouse"></a>取得し、Parallel Data Warehouse のバックアップ サーバーを構成します。
この記事では、Analytics Platform System (APS) および並列データ ウェアハウス (PDW) のバックアップと復元機能で使用するためのバックアップ サーバーとして非アプライアンスの Windows システムを構成する方法について説明します。  
  
  
## <a name="Basics"></a>Backup server の基礎  
バックアップ サーバー:  
  
-   提供され、IT チームによって管理されています。  
  
-   すべての PDW に固有のソフトウェアやツールは必要ありません。 PDW では、バックアップ サーバー上にすべてのソフトウェアはインストールされません。  
  
-   非アプライアンス ラックにあるおよび APS アプライアンス内に配置することはできません。  
  
-   アプライアンスの InfiniBand ネットワークに接続できます。 InfiniBand または; イーサネット経由でバックアップを実行することができます。パフォーマンス上の理由には、InfiniBand を使用することをお勧めします。  
  
-   アプライアンスのドメインではなく、独自の顧客ドメインです。 顧客のドメインとアプライアンスのドメインと信頼関係はありません。  
  
-   バックアップ ファイルの共有、サーバー メッセージ ブロック (SMB) のアプリケーション レベルのネットワーク プロトコルを使用している Windows ファイル共有をホストします。 バックアップ ファイルの共有アクセス許可の付与 (通常、これは、専用のバックアップのユーザー)、Windows ドメイン ユーザーのバックアップを実行し、復元操作は、共有で機能します。 PDW のバックアップを実行して復元操作でバックアップ ファイルの共有できるように、PDW の Windows ドメイン ユーザーのユーザー名とパスワードの資格情報が格納されます。  
  
## <a name="Step1"></a>手順 1:容量の要件を決定します。  
Backup server のシステム要件は、独自のワークロードにほぼ完全に依存します。 購入またはバックアップ サーバーをプロビジョニングする前に、容量の要件を把握する必要があります。 Backup server は、ワークロードのパフォーマンスとストレージの要件を処理する限りにのみ、バックアップを専用にする必要はありません。 複数のバックアップ サーバーをバックアップし、複数のサーバーのいずれかに各データベースを復元するためにすることもできます。  
  
使用して、[バックアップ サーバー容量の計画ワークシート](backup-capacity-planning-worksheet.md)容量の要件を確認するためです。  
  
## <a name="Step2"></a>手順 2:サーバーのバックアップの取得します。  
これで、容量の要件をより深く理解するには、サーバーとのネットワーク コンポーネントを購入またはプロビジョニングする必要がありますを計画できます。 次の要件の一覧を購入の計画に組み込むと、サーバーを購入するか、既存のサーバーをプロビジョニングします。  
  
### <a name="software-requirements"></a>ソフトウェア要件  
Windows ファイル共有 (SMB) プロトコルを使用してファイル サーバー。  
  
Windows Server 2012 をお勧めまたは超えるには。  
  
-   SMB 経由でファイルの事前割り当てのパフォーマンスの利点を取得します。  
  
-   バックアップ操作用のファイルの瞬時初期化 (IFI) を使用します。 IT チームは、サーバーのバックアップでは、この設定を管理します。 PDW 構成マネージャー (dwconfig.exe) の設定または IFI の control 権限、サーバーのバックアップはできません。 Windows の以前のバージョンでは、IFI ではありませんが、バックアップ サーバーとしても使用できます。  
  
### <a name="networking-requirements"></a>ネットワーク要件  
必須ではありませんが、InfiniBand、Backup server の推奨される接続型です。 アプライアンスの InfiniBand ネットワークに読み込みサーバーを接続する準備。  
  
1.  計画、サーバーのラックを閉じて、アプライアンスに十分な InfiniBand スイッチ アプライアンスに接続することができます。 InfiniBand の Mellanox テクノロジの詳細については、ホワイト ペーパーを参照してください。 [InfiniBand 概要](https://www.mellanox.com/pdf/whitepapers/IB_Intro_WP_190.pdf)します。  
  
2.  Mellanox connectx-3 FDR InfiniBand シングルまたはデュアル ポートのネットワーク アダプターを購入します。 データ転送中にフォールト トレランスのための 2 つのポートを持つネットワーク アダプターを購入することをお勧めします。 2 つのポートのネットワーク アダプターが高可用性のために必要です。  
  
3.  デュアル ポート カードは、FDR InfiniBand 2 本のケーブルまたは 1 つのポートのカードの 1 の FDR InfiniBand ケーブルを購入します。 FDR InfiniBand ケーブルでは、読み込みのサーバーをアプライアンスの InfiniBand ネットワークに接続します。 ケーブルの長さは、環境に従ってに読み込み、サーバーとアプライアンスの InfiniBand スイッチ間の距離によって異なります。  
  
## <a name="Step3"></a>手順 3:サーバーの InfiniBand ネットワークに接続します。  
読み込みサーバーの InfiniBand ネットワークを接続するのにには、次の手順を使用します。 サーバーが、InfiniBand ネットワークを使用していない場合は、この手順をスキップします。  
  
1.  ラック、サーバーを閉じてアプライアンスに十分なために、アプライアンスの InfiniBand ネットワークに接続することができます。  
  
2.  読み込みサーバーに、InfiniBand Mellanox connectx-3 FDR InfiniBand ネットワーク アダプターをインストールします。  
  
3.  アプライアンスの最初のラック内の 2 つの InfiniBand スイッチの 1 つに、InfiniBand ネットワーク アダプターを接続するのにには、FDR ケーブルを使用します。  
  
4.  インストールし、InfiniBand ネットワーク アダプターの適切な Windows ドライバーを構成します。  
  
    -   Windows 用の InfiniBand ドライバーは、OpenFabrics Alliance、InfiniBand ベンダーに業界コンソーシアムによって開発されています。  適切なドライバーは、InfiniBand ネットワーク アダプターに配布されたことがあります。 それ以外の場合は、ドライバーは www.openfabrics.org からダウンロードできます。  
  
5.  ネットワーク アダプターの InfiniBand と DNS の設定を構成します。 構成手順については、次を参照してください。 [InfiniBand ネットワーク アダプターの構成](configure-infiniband-network-adapters.md)します。  
  
## <a name="Step4"></a>手順 4:バックアップ ファイル共有を構成します。  
PDW は、UNC ファイル共有のバックアップ サーバーにアクセスします。 ファイル共有を設定します。  
  
1.  バックアップを保存するバックアップ サーバー上のフォルダーを作成します。  
  
2.  バックアップ フォルダーのバックアップの共有と呼ばれる、ファイル共有を作成します。  
  
3.  バックアップと復元を実行するために使用する顧客のドメインに Windows ドメイン アカウントを作成または指定します。 セキュリティ上の理由は、バックアップのユーザーとして専用のアカウントを使用することをお勧めします。  
  
4.  バックアップへのアクセス許可が共有するため、信頼されたアカウントとドメインのバックアップ アカウントのみがアクセスできる、読み取り、および共有の場所への書き込みを追加します。  
  
5.  PDW へのバックアップ ドメイン アカウントの資格情報を追加します。  
  
    以下に例を示します。  
  
    ```sql  
    EXEC sp_pdw_add_network_credentials '10.192.147.63', 'seattle\david', '********';  
    ```  
  
    詳細については、これらのストアド プロシージャを参照してください。  
  
    -   [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)  
  
    -   [sp_pdw_remove_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md)  
  
## <a name="Step5"></a>手順 5:データのバックアップを開始します。  
バックアップ サーバーにデータのバックアップを開始する準備が整いました。  
  
コマンドには、データのバックアップではクエリ クライアントを使用して SQL Server PDW に接続し、バックアップ データベースまたはデータベースの復元を送信します。 ディスクを使用して、バックアップ サーバーとバックアップの場所を指定する句を = です。  
  
> [!IMPORTANT]  
> サーバーのバックアップの InfiniBand IP アドレスを使用してください。 それ以外の場合、データは、InfiniBand ではなくイーサネット経由でコピーされます。  
  
以下に例を示します。  
  
```sql  
BACKUP DATABASE Invoices TO DISK = '\\10.172.14.255\backups\yearly\Invoices2013Full';  
  
RESTORE DATABASE Invoices2013Full  
FROM DISK = '\\10.172.14.255\backups\yearly\Invoices2013Full'  
```  
  
詳細については、以下をご覧ください。 
  
-   [データベースのバックアップ](../t-sql/statements/backup-database-parallel-data-warehouse.md)   
  
-   [RESTORE DATABASE](../t-sql/statements/restore-database-parallel-data-warehouse.md)  
  
## <a name="Security"></a>セキュリティ通知  
サーバーのバックアップはアプライアンスのプライベート ドメインに参加していません。 独自のネットワークであり、独自のドメインとプライベートのアプライアンスのドメイン間に信頼関係はありません。  
  
PDW バックアップはアプライアンスに格納されていない、ため、IT チームはバックアップのセキュリティのすべての側面を管理する責任を負います。 たとえば、データのバックアップ、バックアップの保存に使用するサーバーのセキュリティおよび APS アプライアンスにバックアップ サーバーに接続するネットワーク インフラストラクチャのセキュリティのセキュリティの管理が含まれます。  
  
### <a name="manage-network-credentials"></a>ネットワーク資格情報を管理します。  
  
バックアップ ディレクトリへのネットワーク アクセスは、標準 Windows ファイル共有セキュリティに基づきます。 バックアップを実行する前に作成または、バックアップ ディレクトリに PDW の認証に使用される Windows アカウントを指定する必要があります。 この Windows アカウントには、バックアップ ディレクトリにアクセスし、作成や書き込みを行うための許可を与える必要があります。  
  
> [!IMPORTANT]  
> データのセキュリティ リスクを緩和するために、バックアップ操作と復元操作を実行する目的のためだけに Windows アカウントを 1 つ用意することをお勧めします。 そのアカウントのアクセス許可をバックアップの場所に限定します。  
  
PDW では、ユーザー名とパスワードを保存を使用して、 [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)ストアド プロシージャ。 PDW では、Windows 資格情報マネージャーを使用して、コントロールのノードのユーザー名とパスワードを暗号化およびコンピューティング ノードを格納します。 資格情報は BACKUP DATABASE コマンドでバックアップされません。  
  
PDW からネットワーク資格情報を削除するには、使用、 [sp_pdw_remove_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md)ストアド プロシージャ。  
  
すべての SQL Server PDW に格納されているネットワーク資格情報を一覧表示するには使用、 [sys.dm_pdw_network_credentials](../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md)動的管理ビュー。  
  
### <a name="secure-communications"></a>セキュリティで保護された通信  
  
読み込みサーバーでの操作には、信頼されている内部ネットワークの外部からのデータをプルする UNC パスを使用できます。 攻撃者がネットワーク上または名前解決に影響する機能では、途中受信したり、PDW に送信されるデータを変更することができます。 これは、改ざんや情報漏えいのリスクを表示します。 改ざんのリスクを軽減するには。

- 接続での署名が必要です。 
- 読み込みサーバーのセキュリティ \ セキュリティ オプションで、次のグループ ポリシー オプションを設定します。Microsoft ネットワーク クライアント:常に通信にデジタル署名します。有効になります。  
  
## <a name="see-also"></a>関連項目  
[バックアップと復元](backup-and-restore-overview.md)  
  
