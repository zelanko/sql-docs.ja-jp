---
title: "SQL Server Integration Services (SSIS) のスケール アウト Support for High Availability |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2405235bcfa09d2cc49e007f4eae6975d9ebf7a5
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="scale-out-support-for-high-availability"></a>高可用性のスケール アウトのサポート

スケール アウト SSIS では、ワーカー側の高可用性を複数のスケール アウト ワーカーとパッケージの実行を通じて提供します。
マスター側の高可用性を実現[Always On の SSIS カタログ](../service/ssis-catalog.md#always-on-for-ssis-catalog-ssisdb)と Windows フェールオーバー クラスター。 スケール アウト マスターの複数のインスタンスは、Windows フェールオーバー クラスターでホストされています。 スケール アウト マスター サービスまたは SSISDB プライマリ ノードでは、サービスまたは SSISDB をセカンダリ ノードは引き続きユーザーの要求を受け入れるし、スケール アウト ワーカーと通信します。 

マスタ側の高可用性を設定するに次の手順に従います。

## <a name="1-prerequisites"></a>1.前提条件
Windows フェールオーバー クラスターを設定します。 手順については、「 [Installing the Failover Cluster Feature and Tools for Windows Server 2012 (Windows Server 2012 のフェールオーバー クラスター機能とツールのインストール)](http://blogs.msdn.com/b/clustering/archive/2012/04/06/10291601.aspx) 」のブログ投稿を参照してください。 すべてのクラスター ノードに機能とツールをインストールする必要があります。

## <a name="2-install-scale-out-master-on-primary-node"></a>2.プライマリ ノードでスケール アウト マスターをインストールします。
スケール アウト マスターのプライマリ ノードでデータベース エンジン サービス、Integration Services、およびスケール アウト マスターをインストールします。 

インストール中、する必要があります。 
### <a name="21-set-the-account-running-scale-out-master-service-to-a-domain-account"></a>2.1 では、ドメイン アカウントにスケール アウト マスター サービスを実行するアカウントを設定します。
このアカウントは、後で Windows フェールオーバー クラスター内のセカンダリ ノード上の SSISDB にアクセスできる必要があります。 スケール アウト マスター サービスと SSISDB が個別にフェールオーバーすることと同じノードでできないがあります。

![HA サーバーの構成](media/ha-server-config.PNG)

### <a name="22-include-scale-out-master-service-dns-host-name-in-the-cns-of-scale-out-master-certificate"></a>2.2 マスターを小数点以下桁数を含めるサービス DNS ホスト名の Cn のスケール アウト マスター証明書にします。

このホスト名は、スケール アウト マスター エンドポイントで使用されます。 

![マスターの HA 構成](media/ha-master-config.PNG)

## <a name="3-install-scale-out-master-on-secondary-node"></a>3.スケール アウト マスターをセカンダリ ノードにインストールします。
スケール アウト マスターのセカンダリ ノードでデータベース エンジン サービス、Integration Services、およびスケール アウト マスターをインストールします。 

プライマリ ノードで同じスケール アウト マスター証明書を使用する必要があります。 プライマリ ノードで、スケール アウト マスター SSL 証明書を秘密キーと共にエクスポートし、セカンダリ ノードで loacl マシンのルート証明書ストアにインストールします。 スケール アウト マスターをインストールするときに、この証明書を選択します。

![HA マスター config 2](media/ha-master-config2.PNG)

> [!Note]
> セカンダリのスケール アウト マスターの操作を繰り返して、複数のスケール アウト マスターのバックアップを設定することができます。

## <a name="4-set-up-ssisdb-always-on"></a>4.常に SSISDB を設定します。

常に上のセットアップに SSISDB がわかるように指示[SSIS カタログ (SSISDB) の Always On](../service/ssis-catalog.md#always-on-for-ssis-catalog-ssisdb)です。

さらに、SSISDB を追加する可用性グループに対して可用性 gourp リスナーを作成する必要があります。 参照してください[可用性グループ リスナーの構成を作成または](../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)です。

## <a name="5-update-scale-out-master-service-configuration-file"></a>5.スケール アウト マスター サービス構成ファイルを更新します。
更新プログラムのスケール アウト マスター サービス構成ファイル、\<ドライバー\>: \Program Files\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config、プライマリとセカンダリ ノードにします。 更新**SqlServerName**に*[可用性グループ リスナーの DNS 名]、[Port]*です。

## <a name="6-enable-package-execution-logging"></a>6.パッケージ実行のログ記録を有効にします。

SSISDB でのログ記録を行うにはログイン**## MS_SSISLogDBWorkerAgentLogin ##**パスワードが自動生成します。 SSISDB のすべてのレプリカのログ記録の動作をするには、次の操作を行います。

### <a name="61-change-the-password-of-msssislogdbworkeragentlogin-on-primary-sql-server"></a>6.1 のパスワードを変更する**## MS_SSISLogDBWorkerAgentLogin ##**プライマリ Sql サーバーにします。
### <a name="62-add-the-login-to-secondary-sql-server"></a>6.2 では、セカンダリ Sql Server にログインを追加します。
### <a name="63-update-connection-string-of-logging"></a>6.3 では、ログ記録の接続文字列を更新します。
[カタログ] のストアド プロシージャを呼び出します。[update_logdb_info] で 

@server_name= '*[可用性グループ リスナーの DNS 名]、[Port]*' 

および@connection_string= ' データ ソース =*[可用性グループ リスナーの DNS 名]*、*[Port]*; Initial Catalog = SSISDB です。ユーザー Id = ## MS_SSISLogDBWorkerAgentLogin ## します。パスワード =*[Password]*];'。

## <a name="7-congifure-scale-out-master-service-role-of-windows-failover-cluster"></a>7.Windows フェールオーバー クラスターのスケール アウト マスターに Congifure サービス ロール

フェールオーバー クラスター マネージャー、スケール アウトのクラスターに接続します。 クラスターを選択し、クリックして**アクション**メニューし**役割の構成しています...**.

表示されたを**高可用性ウィザード**を選択**汎用サービス**で**役割の選択**ページして、SQL Server Integration Services スケール アウト マスター 14.0 で**サービスの選択**ページ。

**クライアント アクセス ポイント** ページで、スケール アウト マスター サービスの DNS ホスト名を入力します。

![高可用性ウィザード 1](media/ha-wizard1.PNG)

ウィザードを終了します。

## <a name="8-update-master-address-in-ssisdb"></a>8.マスター更新 SSISDB のアドレス

プライマリ SQL Server では、ストアド プロシージャ [SSIS] を実行します。[カタログ] です。[update_master_address] パラメーターを持つ@MasterAddress= N'https://[スケール アウト マスター サービスの DNS ホスト名]: [マスター Port]'。 

## <a name="9-add-scale-out-worker"></a>9.スケール アウト ワーカーを追加します。

利用してスケール アウト ワーカーを追加するようになりました、[スケール アウト Manager](integration-services-ssis-scale-out-manager.md)です。 入力*[SQL Server 可用性グループ リスナーの DNS 名]*、*[Port]*接続ページ。





