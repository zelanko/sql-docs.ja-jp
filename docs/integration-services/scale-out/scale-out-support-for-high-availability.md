---
title: "高可用性を実現するための SQL Server Integration Services (SSIS) Scale Out のサポート | Microsoft Docs"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2202b61a9efce26edb0edcef53204351338ecee6
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="scale-out-support-for-high-availability"></a>高可用性を実現するための Scale Out のサポート

SSIS Scale Out では、複数の Scale Out Worker を使用してパッケージを実行することで、ワーカー側の高可用性が提供されます。
マスター側の高可用性は、[Always On for SSIS Catalog](../service/ssis-catalog.md#always-on-for-ssis-catalog-ssisdb) と Windows フェールオーバー クラスターにより実現されます。 Scale Out Master の複数のインスタンスは、Windows フェールオーバー クラスターでホストされています。 プライマリ ノードの Scale Out Master サービスまたは SSISDB がダウンすると、セカンダリ ノードのサービスまたは SSISDB が引き続きユーザーの要求を受け入れて、Scale Out Worker と通信します。 

マスター側の高可用性を設定するには、次の手順に従います。

## <a name="1-prerequisites"></a>1.前提条件
Windows フェールオーバー クラスターを設定します。 手順については、「 [Installing the Failover Cluster Feature and Tools for Windows Server 2012 (Windows Server 2012 のフェールオーバー クラスター機能とツールのインストール)](http://blogs.msdn.com/b/clustering/archive/2012/04/06/10291601.aspx) 」のブログ投稿を参照してください。 すべてのクラスター ノードに機能とツールをインストールする必要があります。

## <a name="2-install-scale-out-master-on-primary-node"></a>2.プライマリ ノードに Scale Out Master をインストールする
Scale Out Master のプライマリ ノードにデータベース エンジン サービス、Integration Services、および Scale Out Master をインストールします。 

インストール時に、次のことを行う必要があります。 
### <a name="21-set-the-account-running-scale-out-master-service-to-a-domain-account"></a>2.1 ドメイン アカウントに Scale Out Master サービスを実行するアカウントを設定します。
このアカウントは、後で Windows フェールオーバー クラスター内のセカンダリ ノード上の SSISDB にアクセスできる必要があります。 Scale Out Master サービスと SSISDB は個別にフェールオーバーできるため、同じノードにない場合があります。

![HA サーバーの構成](media/ha-server-config.PNG)

### <a name="22-include-scale-out-master-service-dns-host-name-in-the-cns-of-scale-out-master-certificate"></a>2.2 Scale Out Master サービス DNS ホスト名を Scale Out Master 証明書の CN に含めます。

このホスト名は、Scale Out Master エンドポイントで使用されます。 

![HA マスターの構成](media/ha-master-config.PNG)

## <a name="3-install-scale-out-master-on-secondary-node"></a>3.セカンダリ ノードに Scale Out Master をインストールする
Scale Out Master のセカンダリ ノードにデータベース エンジン サービス、Integration Services、および Scale Out Master をインストールします。 

プライマリ ノードと同じ Scale Out Master 証明書を使用する必要があります。 プライマリ ノードで、Scale Out Master SSL 証明書を秘密キーと共にエクスポートし、セカンダリ ノード上のローカル マシンのルート証明書ストアにインストールします。 Scale Out Master をインストールするときに、この証明書を選択します。

![HA マスターの構成 2](media/ha-master-config2.PNG)

> [!Note]
> セカンダリ Scale Out Master の操作を繰り返すことで、複数の Scale Out Master のバックアップを設定できます。

## <a name="4-set-up-ssisdb-always-on"></a>4.SSISDB Always On を設定する

SSISDB の Always On を設定する手順は、「[Always On for SSIS Catalog (SSISDB)](../service/ssis-catalog.md#always-on-for-ssis-catalog-ssisdb)」に記載されています。

さらに、SSISDB を追加する可用性グループに対して可用性グループ リスナーを作成する必要があります。 「[可用性グループ リスナーの作成または構成](../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)」を参照してください。

## <a name="5-update-scale-out-master-service-configuration-file"></a>5.Scale Out Master サービス構成ファイルを更新する
プライマリ ノードとセカンダリ ノードで、Scale Out Master サービス構成ファイル \<ドライバー\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config を更新します。 **SqlServerName** を *[Availability Group Listener DNS name],[Port]* に更新します。

## <a name="6-enable-package-execution-logging"></a>6.パッケージ実行のログ記録を有効にする

SSISDB でのログ記録は、ログイン **##MS_SSISLogDBWorkerAgentLogin##** (パスワードは自動生成されます) によって行われます。 SSISDB のすべてのレプリカのログ記録を機能させるには、次の操作を行います。

### <a name="61-change-the-password-of-msssislogdbworkeragentlogin-on-primary-sql-server"></a>6.1 プライマリ SQL Server で **##MS_SSISLogDBWorkerAgentLogin##** のパスワードを変更します。
### <a name="62-add-the-login-to-secondary-sql-server"></a>6.2 ログインをセカンダリ SQL Server に追加します。
### <a name="63-update-connection-string-of-logging"></a>6.3 ログ記録の接続文字列を更新します。
次を使用して、ストアド プロシージャ [catalog].[update_logdb_info] を呼び出します。 

@server_name = '*[Availability Group Listener DNS name],[Port]*' 

および @connection_string = 'Data Source=*[Availability Group Listener DNS name]*,*[Port]*;Initial Catalog=SSISDB;User Id=##MS_SSISLogDBWorkerAgentLogin##;Password=*[Password]*];'

## <a name="7-congifure-scale-out-master-service-role-of-windows-failover-cluster"></a>7.Windows フェールオーバー クラスターの Scale Out Master サービス ロールを構成する

フェールオーバー クラスター マネージャーで、Scale Out のクラスターに接続します。クラスターを選択し、メニューで **[アクション]**、**[ロールの構成]** の順にクリックします。

表示される**高可用性ウィザード**の **[ロールの選択]** ページで **[汎用サービス]** を選択し、**[サービスの選択]** ページで [SQL Server Integration Services Scale Out Master 14.0] を選択します。

**[クライアント アクセス ポイント]** ページで、Scale Out Master サービスの DNS ホスト名を入力します。

![HA ウィザード 1](media/ha-wizard1.PNG)

ウィザードを終了します。

## <a name="8-update-master-address-in-ssisdb"></a>8.SSISDB でマスター アドレスを更新する

プライマリ SQL Server で、ストアド プロシージャ [SSIS].[catalog].[update_master_address] をパラメーター @MasterAddress = N'https://[Scale Out Master service DNS host name]:[Master Port]' を使用して実行します。 

## <a name="9-add-scale-out-worker"></a>9.Scale Out Worker を追加する

これで、[Scale Out Manager](integration-services-ssis-scale-out-manager.md) を使用して、Scale Out Worker を追加できます。 接続ページで、*[SQL Server Availability Group Listener DNS name]*,*[Port]* を入力します。




