---
title: 取得および APS PDW のサーバーのバックアップを構成します。
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: ''
ms.technology: mpp-data-warehouse
description: アプライアンス非 Windows システム バックアップで使用するサーバーのバックアップとして構成し、Analytics Platform System (APS) および SQL Server 並列データ ウェアハウス (PDW) 機能を復元します。
ms.date: 10/20/2016
ms.topic: article
caps.latest.revision: 20
ms.assetid: f8b769fe-c864-4d65-abcb-a9a287061702
ms.openlocfilehash: 564a70d5fa483f2c34ef2598213a2c22074daf80
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="acquire-and-configure-a-backup-server"></a>取得して、サーバーのバックアップを構成します。
このトピックでは、Analytics Platform System (APS) でのバックアップと復元の機能で使用するサーバーのバックアップおよび SQL Server 並列データ ウェアハウス (PDW) としてアプライアンス非 Windows システムを構成する方法について説明します。  
  
  
## <a name="Basics"></a>サーバーのバックアップの基礎  
サーバーのバックアップ:  
  
-   提供され、IT チームで管理します。  
  
-   すべての PDW に固有のソフトウェアやツールは必要ありません。 PDW では、バックアップ サーバー上にあるソフトウェアはインストールされません。  
  
-   非アプライアンス ラック内にあるし、APS アプライアンス内に配置することはできません。  
  
-   アプライアンスの InfiniBand ネットワークに接続できます。 InfiniBand やイーサネット; 経由でバックアップを実行することができます。パフォーマンス上の理由には、InfiniBand を使用することをお勧めします。  
  
-   独自のユーザー ドメイン、アプライアンス ドメインではなくです。 顧客のドメインとアプライアンス間に信頼関係はありません。  
  
-   これは Windows ファイル共有サーバー メッセージ ブロック (SMB) のアプリケーション レベルのネットワーク プロトコルを使用するバックアップ ファイル共有をホストします。 バックアップ ファイル共有のアクセス許可を与える Windows ドメイン ユーザー (通常これは、専用のバックアップのユーザー) のバックアップを実行し、復元操作は、共有で機能します。 Windows ドメイン ユーザーのユーザー名とパスワードの資格情報は、PDW がバックアップを実行して、バックアップ ファイル共有での操作を復元できるように、PDW に格納されます。  
  
## <a name="Step1"></a>手順 1: 容量の要件を確認します。  
バックアップ サーバーのシステム要件は、独自のワークロードにほぼ完全に依存します。 購入またはバックアップ サーバーをプロビジョニングする前に、容量の要件を確認する必要があります。 サーバーのバックアップは、ワークロードのパフォーマンスおよび記憶域の要件を処理する限り、バックアップのみを目的でのみ使用する必要はありません。 複数のバックアップ サーバーをバックアップして、複数のサーバーのいずれかに各データベースを復元するためにすることもできます。  
  
使用して、[バックアップ サーバー容量の計画ワークシート](backup-capacity-planning-worksheet.md)容量の要件を特定するためです。  
  
## <a name="Step2"></a>手順 2: サーバーのバックアップを取得します。  
これで、容量の要件をより深く理解するには、購入するか、プロビジョニングする必要がありますのネットワーク コンポーネントとサーバーを計画できます。 次の要件の一覧を購入プランに組み込むと、サーバーを購入するか、既存のサーバーをプロビジョニングします。  
  
### <a name="software-requirements"></a>ソフトウェア要件  
任意のファイル サーバー、Windows ファイル共有 (SMB) プロトコルを使用します。  
  
Windows Server 2012 をお勧めまたはに超える。  
  
-   SMB 経由でファイルの事前割り当てのパフォーマンスの利点を取得します。  
  
-   バックアップ操作を瞬時ファイル初期化 (IFI) を使用します。 社内の IT チームは、サーバーのバックアップでは、この設定を管理します。 PDW 構成マネージャー (dwconfig.exe) を設定したりしない IFI、バックアップ サーバーの control 権限。 Windows の以前のバージョンでは、IFI はありませんが、バックアップ サーバーとしても使用できます。  
  
### <a name="networking-requirements"></a>ネットワーク要件  
必須ではありませんが、InfiniBand、バックアップ サーバーの推奨される接続型です。 アプライアンスの InfiniBand ネットワークにサーバーを読み込んでを接続するための準備。  
  
1.  サーバーのラックに計画 InfiniBand スイッチ アプライアンスに接続するように、アプライアンスに十分な数を閉じます。 InfiniBand の Mellanox テクノロジの詳細については、ホワイト ペーパーを参照してください。 [InfiniBand 概要](http://www.mellanox.com/pdf/whitepapers/IB_Intro_WP_190.pdf)です。  
  
2.  Mellanox connectx-3 FDR InfiniBand 1 または 2 台のポートのネットワーク アダプターを購入します。 データ転送中にフォールト トレランスのための 2 つのポートを持つネットワーク アダプターを購入することをお勧めします。 2 つのポートのネットワーク アダプターが、高可用性のため必要です。  
  
3.  デュアル ポート カードは、2 つの FDR InfiniBand ケーブルまたは 1 つのポートのカードの 1 の FDR InfiniBand ケーブルを購入します。 FDR InfiniBand ケーブルでは、サーバーを読み込んでをアプライアンスの InfiniBand ネットワークに接続します。 ケーブルの長さは、お客様の環境に応じて読み込みサーバーとアプライアンス InfiniBand スイッチ間の距離とは異なります。  
  
## <a name="Step3"></a>手順 3: InfiniBand ネットワークにサーバーを接続します。  
読み込みサーバーの InfiniBand ネットワークに接続するのにには、次の手順を使用します。 サーバーがの InfiniBand ネットワークを使用していない場合は、この手順をスキップします。  
  
1.  ラック、サーバーの状態アプライアンスに十分アプライアンスの InfiniBand ネットワークに接続することができるようにします。  
  
2.  InfiniBand Mellanox connectx-3 FDR InfiniBand ネットワーク アダプターを読み込むサーバーにインストールします。  
  
3.  最初のアプライアンス ラック内で 2 つの InfiniBand スイッチのいずれかに InfiniBand ネットワーク アダプターを接続するのにには、FDR ケーブルを使用します。  
  
4.  インストールし、適切な Windows ドライバー InfiniBand ネットワーク アダプターを構成します。  
  
    -   Windows 用の InfiniBand ドライバーは、OpenFabrics Alliance、InfiniBand 仕入先の業界 consortium によって開発されています。  適切なドライバーは、InfiniBand ネットワーク アダプターに配布された可能性があります。 それ以外の場合は、ドライバーは www.openfabrics.org からダウンロードできます。  
  
5.  ネットワーク アダプターの InfiniBand と DNS の設定を構成します。 構成手順については、次を参照してください。 [InfiniBand ネットワーク アダプターの構成](configure-infiniband-network-adapters.md)です。  
  
## <a name="Step4"></a>手順 4: 構成のバックアップ ファイルの共有  
PDW では、サーバーのバックアップを UNC ファイル共有を通じてアクセスします。 ファイル共有を設定します。  
  
1.  バックアップを保存するサーバーのバックアップにフォルダーを作成します。  
  
2.  バックアップ共有をバックアップ フォルダー用と呼ばれる、ファイル共有を作成します。  
  
3.  指定または、ユーザー ドメインのバックアップや復元を実行するために使用する Windows ドメイン アカウントを作成します。 セキュリティ上の理由から、バックアップのユーザーとして、専用のアカウントを使用することをお勧めします。  
  
4.  バックアップへのアクセス許可が共有ために信頼されているアカウントとドメインのバックアップ アカウントのみがアクセスできますが、読み取り、および共有の場所への書き込みを追加します。  
  
5.  PDW へのバックアップ ドメイン アカウントの資格情報を追加します。  
  
    以下に例を示します。  
  
    ```sql  
    EXEC sp_pdw_add_network_credentials '10.192.147.63', 'seattle\david', '********';  
    ```  
  
    詳細については、これらのストアド プロシージャを参照してください。  
  
    -   [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)  
  
    -   [sp_pdw_remove_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md)  
  
## <a name="Step5"></a>手順 5: データのバックアップを開始します。  
バックアップ サーバーにデータのバックアップを開始する準備が整いました。  
  
データのバックアップではクエリ クライアントを使用して SQL Server PDW に接続し、バックアップ データベースまたはデータベースの復元を送信するには、次のようにコマンドします。 ディスクを使用してバックアップ サーバーおよびバックアップの場所を指定する句を = です。  
  
> [!IMPORTANT]  
> サーバーのバックアップの InfiniBand IP アドレスを使用してください。 それ以外の場合、データは、InfiniBand の代わりにイーサネット上にコピーされます。  
  
以下に例を示します。  
  
```sql  
BACKUP DATABASE Invoices TO DISK = '\\10.172.14.255\backups\yearly\Invoices2013Full';  
  
RESTORE DATABASE Invoices2013Full  
FROM DISK = '\\10.172.14.255\backups\yearly\Invoices2013Full'  
```  
  
詳細については、以下をご覧ください。 
  
-   [BACKUP DATABASE](../t-sql/statements/backup-database-parallel-data-warehouse.md)   
  
-   [データベースを復元します。](../t-sql/statements/restore-database-parallel-data-warehouse.md)  
  
## <a name="Security"></a>セキュリティ通知  
サーバーのバックアップは、アプライアンスのプライベート ドメインに参加していません。 独自のネットワーク内にあるし、独自のドメインとプライベートのアプライアンス ドメイン間の信頼関係がありません。  
  
アプライアンス上 PDW バックアップが格納されていないので、社内の IT チームは、バックアップのセキュリティのすべての側面を管理するため役割です。 たとえば、データのバックアップ、バックアップを保存するために使用するサーバーのセキュリティおよびサーバーのバックアップを APS アプライアンスに接続するネットワーク インフラストラクチャのセキュリティのセキュリティの管理が含まれます。  
  
### <a name="manage-network-credentials"></a>ネットワーク資格情報を管理します。  
  
バックアップ ディレクトリへのネットワーク アクセスは、標準 Windows ファイル共有セキュリティに基づきます。 バックアップを実行する前に作成または、バックアップ ディレクトリに PDW の認証に使用される Windows アカウントを指定する必要があります。 この Windows アカウントには、バックアップ ディレクトリにアクセスし、作成や書き込みを行うための許可を与える必要があります。  
  
> [!IMPORTANT]  
> データのセキュリティ リスクを緩和するために、バックアップ操作と復元操作を実行する目的のためだけに Windows アカウントを 1 つ用意することをお勧めします。 そのアカウントのアクセス許可をバックアップの場所に限定します。  
  
PDW では、ユーザー名とパスワードを保存を使用して、 [sp_pdw_add_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)ストアド プロシージャです。 PDW では、格納、コントロールのノード上のユーザー名とパスワードの暗号化し、コンピューティング ノードに Windows 資格情報マネージャーを使用します。 資格情報は BACKUP DATABASE コマンドでバックアップされません。  
  
PDW からネットワーク資格情報を削除するには、使用、 [sp_pdw_remove_network_credentials](../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md)ストアド プロシージャです。  
  
すべての SQL Server PDW に格納されているネットワーク資格情報の一覧を表示、使用、 [sys.dm_pdw_network_credentials](../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md)動的管理ビュー。  
  
### <a name="secure-communications"></a>セキュリティで保護された通信  
  
読み込みサーバー上の操作は、信頼されている内部ネットワークの外部からのプル データへの UNC パスを使用できます。 攻撃者がネットワーク上または名前解決に影響する機能では、途中受信したり、PDW に送信されるデータを変更することができます。 これは、改ざんや情報の漏えいリスクを表示します。 改ざんのリスクを軽減するためには。

- 接続での署名が必要です。 
- 読み込みサーバーのセキュリティ の順に展開したオプションで、次のグループ ポリシー オプションを設定します。 Microsoft ネットワーク クライアント: 常に通信にデジタル署名: 有効になっています。  
  
## <a name="see-also"></a>参照  
[バックアップと復元](backup-and-restore-overview.md)  
  
