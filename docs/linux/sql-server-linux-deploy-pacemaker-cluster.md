---
title: "SQL Server on Linux のペース クラスターの展開 |Microsoft ドキュメント"
description: "このチュートリアルでは、SQL Server on Linux のペース クラスターを展開する方法を示します。"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 12/11/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.workload: On Demand
ms.openlocfilehash: dd9d35a7fa6e8a8a0e826d584a4f78ca2581d9bc
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="deploy-a-pacemaker-cluster-for-sql-server-on-linux"></a>SQL Server on Linux のペース クラスターを展開します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このチュートリアルのドキュメントの Linux ペース クラスターを展開に必要なタスク、 [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Always On 可用性グループ (AG) またはフェールオーバー クラスター インスタンス (FCI)。 密に結合された Windows Server とは異なり/[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]前に、またはのインストール後、スタック ペース クラスターの作成に加え、Linux 上の可用性グループ (AG) の構成を行うことができます[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]です。 クラスターを構成した後、統合とペース部分では、可用性グループまたは FCI の展開のリソースの構成は行われます。
> [!IMPORTANT]
> クラスター型なしの可用性グループは*いない*ペース クラスターでは、必要なもそのペースで管理することができます。 

> [!div class="checklist"]
> * 高可用性アドオンをインストールし、ペースをインストールします。
> * ペース (RHEL および Ubuntu のみ) 用のノードを準備します。
> * ペース クラスターを作成します。
> * SQL Server HA と SQL Server エージェントのパッケージをインストールします。
 
## <a name="prerequisite"></a>前提条件
[SQL Server 2017 インストール](sql-server-linux-setup.md)です。

## <a name="install-the-high-availability-add-on"></a>高可用性アドオンをインストールします。
Linux の各配布用の高可用性 (HA) アドオンを構成するパッケージをインストールするのにには、次の構文を使用します。 

**Red Hat Enterprise Linux (RHEL)**
1.  次の構文を使用してサーバーを登録します。 有効なユーザー名とパスワードを求められます。
    
    ```bash
    sudo subscription-manager register
    ```
    
2.  登録の使用可能なプールの一覧を表示します。
    
    ```bash
    sudo subscription-manager list --available
3.  Run the following command to associate RHEL high availability with the subscription
    
    ```bash
    sudo subscription-manager attach --pool=<PoolID>
    ```
    
    ここで*PoolId*前の手順から高可用性サブスクリプション プール id を指定します。
    
4.  高可用性のアドオンを使用することができるリポジトリを有効にします。
    
    ```bash
    sudo subscription-manager repos --enable=rhel-ha-for-rhel-7-server-rpms
    ```
    
5.  ペースをインストールします。
    
    ```bash
    sudo yum install pacemaker pcs fence-agents-all resource-agents
    ```

**Ubuntu**

```bash
sudo apt-get install pacemaker pcs fence-agents resource-agents
```

**SUSE Linux Enterprise Server (SLES)**

YaST で高可用性のパターンをインストールまたはサーバーの主なインストールの一部として実行します。 ソースとして、またはオンライン取得することによって、ISO または DVD をインストールを実行できます。
> [!NOTE]
> SLES、HA アドオンを取得、クラスターの作成時に初期化します。

## <a name="prepare-the-nodes-for-pacemaker-rhel-and-ubuntu-only"></a>ペース (RHEL および Ubuntu のみ) のノードを準備します。
ペース自体は、という名前の配布で作成されたユーザーを使用して*hacluster*です。 RHEL および Ubuntu に HA アドオンがインストールされているときに、ユーザーが作成されます。
1. ペース クラスターのノードとして使用する各サーバーでは、クラスターで使用するユーザーのパスワードを作成します。 例で使用される名前は*hacluster*が任意の名前を使用できます。 ユーザー名とパスワードをペース クラスターに参加しているすべてのノードで同じにする必要があります。
   
    ```bash
    sudo passwd hacluster
    ```
    
2. ペース クラスターの一部となる各ノードで有効にして、開始、 `pcsd` (RHEL と Ubuntu) は、次のコマンドでサービス。

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   ```
   
   実行し、
   
   ```bash
   sudo systemctl status pcsd
   ```
   
   いることを確認する`pcsd`が開始します。
3. ペース クラスターの考えられる各ノードのペース サービスを有効にします。
   
   ```bash
   sudo systemctl start pacemaker
   ```

   Ubuntu では、エラー参照してください。
   
   *既定の開始のペースには、ランレベル、中止が含まれていません。*
   
   このエラーは、既知の問題です。 エラーに関係なくペース サービスを有効にすると成功し、このバグがある時点で今後修正できます。
   
4. 次に、作成し、ペース クラスターを起動します。 この手順で RHEL と Ubuntu の間で 1 つの相違があります。 両方の配布中に次のようにインストールします。 `pcs` RHEL、このコマンドを実行する上で、ペース クラスターの既存の構成を破棄するのは、既定の構成ファイルを構成し、新しいクラスターを作成します。

<a id="create"></a>
## <a name="create-the-pacemaker-cluster"></a>ペース クラスターを作成します。 
このセクションでは、それぞれの Linux ディストリビューションのクラスターを作成および構成方法を説明します。

**RHEL**

1. ノードを承認します。
   
   ```bash
   sudo pcs cluster auth <Node1 Node2 … NodeN> -u hacluster
   ```
   
   ここで*NodeX*ノードの名前を指定します。
2. クラスターを作成します。
   
   ```bash
   sudo pcs cluster setup --name <PMClusterName Nodelist> --start --all --enable
   ```
   
   ここで*PMClusterName*ペース クラスターに割り当てられた名前と*Nodelist*をスペースで区切られたノードの名前の一覧を示します。

**Ubuntu**

Ubuntu の構成は、RHEL に似ています。 ただし、1 つの主要な相違がある: クラスター、および有効と開始の基本構成を作成するペース パッケージをインストールする`pcsd`です。 エラーが発生した場合は、RHEL 説明下手順に従って正確にペース クラスターを構成しようとすると、します。 この問題を解決するには、次の手順を実行します。 
1. 各ノードからペースの既定の構成を削除します。
   
   ```bash
   sudo pcs cluster destroy
   ```
   
2. ペース クラスターの作成に RHEL セクションの手順に従います。

**SLES**

ペース クラスターを作成するプロセスは、完全に異なる sles RHEL および Ubuntu 上にあります。 次の手順は、SLES でクラスターを作成する方法を文書化します。
1. 実行して、クラスター構成プロセスを開始します。 
   ```bash
   sudo ha-cluster-init
   ``` 
   
   ノードのいずれか。 NTP が構成されていないことと、ウォッチドッグのデバイスが検出されないことを求められます。 処理の準備と実行の大丈夫です。 ウォッチドッグは、ストレージ ベースである SLES の組み込みのフェンス操作を使用する場合、STONITH に関連付けられます。 NTP とウォッチドッグを後で構成することができます。
   
2. Corosync の構成を求められます。 マルチキャスト アドレスおよびポートだけでなく、バインドするネットワーク アドレスに対して求められます。 ネットワーク アドレスが使用されます。 サブネットです。たとえば、192.191.190.0 です。 すべてのプロンプトで、既定値をそのまま使用したり、必要に応じて変更できます。
   
3. 次に、ディスク ベース フェンス操作は、SBD を構成するかどうかを求められます。 この構成は、必要な場合は、後で行うことができます。 SBD がない場合、設定されているとは異なり RHEL および Ubuntu、`stonith-enabled`は既定で false に設定します。
   
4. 最後に、管理用の IP アドレスを構成するかどうかを求められます。 この IP アドレス オプションですが、関数を使用して高可用性 Web Konsole (ホーク) に接続するために使用するためにクラスターの IP アドレスを作成するという意味での Windows Server フェールオーバー クラスター (WSFC) の IP アドレスに似ています。 この構成はオプションです。
   
5. その後、クラスターが立ち上がっており実行中を発行して 
   ```bash
   sudo crm status
   ```
   
6. 変更、 *hacluster*を使用してパスワード 
   ```bash
   sudo passwd hacluster
   ```
   
7. 管理用の IP アドレスを構成した場合も、パスワードの変更をテストするブラウザーでテストできます*hacluster*です。
   ![](./media/sql-server-linux-deploy-pacemaker-cluster/image2.png)
   
8. クラスターのノードになる別の SLES サーバー上で実行します。 
   ```bash
   sudo ha-cluster-join
   ```
   
9. メッセージが表示されたらは、名前または前の手順では、クラスターの最初のノードとして構成されたサーバーの IP アドレスを入力します。 サーバーは、既存のクラスターにノードとして追加されます。
   
10. 発行することによって、ノードが追加されたことを確認します。 
   ```bash
   sudo crm status
   ```
   
11. 変更、 *hacluster*を使用してパスワード 
   ```bash
   sudo passwd hacluster
   ```
   
12. クラスターに追加する手順の他のすべてのサーバーに対して 8. ~ 11. を繰り返します。

## <a name="install-the-sql-server-ha-and-sql-server-agent-packages"></a>SQL Server HA と SQL Server エージェントのパッケージをインストールします。
次のコマンドを使用して、SQL Server HA パッケージをインストールして[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]エージェント、既にインストールされていない場合。 インストール後に HA パッケージをインストールする[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]の再起動が必要[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]を使用するのには、します。 これらの手順は、マイクロソフトのパッケージのリポジトリが既に設定されている、ので前提としています。[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]この時点でインストールする必要があります。
> [!NOTE]
> - 使用しない場合[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]ログ配布やその他の用途のエージェントがないインストールするためにパッケージ化*mssql server エージェント*スキップすることができます。
> - その他の省略可能なパッケージは、 [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Linux では、 [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] 、フルテキスト検索 (*mssql サーバー-fts*) および[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Integration Services (*mssql サーバーが*)、されません。FCI は、または、AG のいずれかの高可用性のために必要です。

**RHEL**

```bash
sudo yum install mssql-server-ha mssql-server-agent
sudo systemctl restart mssql-server
```

**Ubuntu**

```bash
sudo apt-get install mssql-server-ha mssql-server-agent
sudo systemctl restart mssql-server
```

**SLES**

```bash
sudo zypper install mssql-server-ha mssql-server-agent
sudo systemctl restart mssql-server
```

## <a name="next-steps"></a>次の手順

このチュートリアルでは、SQL Server on Linux のペース クラスターを展開する方法について学習しました。 方法を学習します。
> [!div class="checklist"]
> * 高可用性アドオンをインストールし、ペースをインストールします。
> * ペース (RHEL および Ubuntu のみ) 用のノードを準備します。
> * ペース クラスターを作成します。
> * SQL Server HA と SQL Server エージェントのパッケージをインストールします。

作成し、Linux 上の SQL Server の可用性グループの構成を参照してください。

> [!div class="nextstepaction"]
> [作成し、Linux 上の SQL Server の可用性グループを構成する](sql-server-linux-create-availability-group.md)です。

