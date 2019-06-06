---
title: SQL Server on Linux の Pacemaker クラスターのデプロイ |Microsoft Docs
description: このチュートリアルでは、SQL Server on Linux の Pacemaker クラスターをデプロイする方法を示します。
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 12/11/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: be1bae381cf9eb07180299130917cb6cbf3bfec3
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66705543"
---
# <a name="deploy-a-pacemaker-cluster-for-sql-server-on-linux"></a>SQL Server on Linux の Pacemaker クラスターをデプロイします。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このチュートリアル用の Linux の Pacemaker クラスターをデプロイに必要なタスクのドキュメントを[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Always On 可用性グループ (AG) またはフェールオーバー クラスター インスタンス (FCI)。 密結合の Windows Server とは異なり/[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]のインストールの前後に、Linux 上の可用性グループ (AG) の構成だけでなく、スタック、Pacemaker クラスターの作成を行うことができます[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]します。 クラスターを構成した後、統合と、Pacemaker 部分では、AG または FCI の展開のリソースの構成が行われます。
> [!IMPORTANT]
> None のクラスターの種類で、AG は*いない*Pacemaker クラスターを必要ともその Pacemaker で管理することができます。 

> [!div class="checklist"]
> * 高可用性アドオンをインストールし、Pacemaker をインストールします。
> * Pacemaker (RHEL および Ubuntu のみ) 用のノードを準備します。
> * Pacemaker クラスターを作成します。
> * SQL Server の HA および SQL Server エージェントのパッケージをインストールします。
 
## <a name="prerequisite"></a>前提条件
[SQL Server 2017 インストール](sql-server-linux-setup.md)します。

## <a name="install-the-high-availability-add-on"></a>高可用性アドオンをインストールします。
Linux の各配布用の高可用性 (HA) アドオンを構成するパッケージをインストールするのにには、次の構文を使用します。 

**Red Hat Enterprise Linux (RHEL)**
1.  次の構文を使用してサーバーを登録します。 有効なユーザー名とパスワードを求められます。
    
    ```bash
    sudo subscription-manager register
    ```
    
2.  登録に使用可能なプールの一覧を表示します。
    
    ```bash
    sudo subscription-manager list --available
    ```

3.  RHEL の高可用性をサブスクリプションに関連付けるには、次のコマンドを実行します。
    
    ```bash
    sudo subscription-manager attach --pool=<PoolID>
    ```
    
    場所*PoolId*は、前の手順から高可用性のサブスクリプションのプールの ID です。
    
4.  高可用性アドオンを使用できるリポジトリを有効にします。
    
    ```bash
    sudo subscription-manager repos --enable=rhel-ha-for-rhel-7-server-rpms
    ```
    
5.  Pacemaker をインストールします。
    
    ```bash
    sudo yum install pacemaker pcs fence-agents-all resource-agents
    ```

**Ubuntu**

```bash
sudo apt-get install pacemaker pcs fence-agents resource-agents
```

**SUSE Linux Enterprise Server (SLES)**

YaST で高可用性のパターンをインストールすることも、サーバーのメインのインストールの一部としての操作を行います。 ソースとして、またはオンライン取得することによって、ISO または DVD をインストールを実行できます。
> [!NOTE]
> HA アドオン SLES、クラスターの作成時に初期化を取得します。

## <a name="prepare-the-nodes-for-pacemaker-rhel-and-ubuntu-only"></a>Pacemaker (RHEL および Ubuntu のみ) 用のノードを準備します。
Pacemaker は、という名前のディストリビューションに作成されたユーザーを使用して*hacluster*します。 HA アドオンが RHEL および Ubuntu にインストールされているときに、ユーザーが作成されます。
1. Pacemaker クラスターのノードとして使用する各サーバーでは、クラスターで使用されるユーザーのパスワードを作成します。 例で使用する名前は*hacluster*が任意の名前を使用できます。 名とパスワードは、Pacemaker クラスターに参加しているすべてのノードで同じである必要があります。
   
    ```bash
    sudo passwd hacluster
    ```
    
2. Pacemaker クラスターの一部となる各ノードで有効にして、開始、`pcsd`サービスに、次のコマンド (RHEL と Ubuntu)。

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   ```
   
   実行し、
   
   ```bash
   sudo systemctl status pcsd
   ```
   
   いることを確認する`pcsd`が開始します。
3. Pacemaker クラスターの各ノード上の Pacemaker サービスを有効にします。
   
   ```bash
   sudo systemctl start pacemaker
   ```

   Ubuntu では、エラー参照してください。
   
   *pacemaker 既定の開始にはには、中止ランレベルが含まれていません。*
   
   このエラーは、既知の問題です。 エラーに関係なくは成功しますが、Pacemaker サービスを有効にしてこのバグをいくつかの時点で、将来修正されます。
   
4. 次に、作成し、Pacemaker クラスターを起動します。 この手順で RHEL と Ubuntu の 1 つの違いがあります。 インストール中には、両方のディストリビューション`pcs`RHEL、このコマンドを実行する上で、Pacemaker クラスターの既存の構成を破棄するために既定の構成ファイルを構成し、新しいクラスターを作成します。

<a id="create"></a>
## <a name="create-the-pacemaker-cluster"></a>Pacemaker クラスターを作成します。 
このセクションでは、作成し、各配布の Linux クラスターを構成する方法を説明します。

**RHEL**

1. ノードを承認します。
   
   ```bash
   sudo pcs cluster auth <Node1 Node2 ... NodeN> -u hacluster
   ```
   
   場所*NodeX*ノードの名前を指定します。
2. クラスターを作成する。
   
   ```bash
   sudo pcs cluster setup --name <PMClusterName Nodelist> --start --all --enable
   ```
   
   場所*PMClusterName* Pacemaker クラスターに割り当てられた名前と*Nodelist*スペースで区切られたノードの名前の一覧を示します。

**Ubuntu**

Ubuntu の構成は、RHEL に似ています。 ただし、1 つの主な違いがある: クラスター、および有効と開始の基本構成を作成して Pacemaker パッケージをインストールする`pcsd`します。 エラーが発生した正確に RHEL の手順に従って、Pacemaker クラスターを構成しようとする場合。 この問題を解決するには、次の手順を実行します。 
1. 各ノードからは、Pacemaker の既定の構成を削除します。
   
   ```bash
   sudo pcs cluster destroy
   ```
   
2. Pacemaker クラスターを作成するための RHEL セクションの手順に従います。

**SLES**

Pacemaker クラスターを作成するためのプロセスがまったく異なる sles RHEL および Ubuntu で実行されるよりもします。 次の手順は、SLES でクラスターを作成する方法を文書化します。
1. 実行して、クラスター構成のプロセスを開始します。 
   ```bash
   sudo ha-cluster-init
   ``` 
   
   ノードのいずれか。 NTP が構成されていないことと、ウォッチドッグのデバイスが検出されないことを求められます可能性があります。 いったい何して実行するために問題はありません。 ストレージ ベースである SLES の組み込みのフェンス操作を使用する場合、ウォッチドッグは STONITH に関連します。 NTP とウォッチドッグは、後で構成することができます。
   
2. Corosync を構成するように求められます。 マルチキャスト アドレスおよびポートと、バインドするネットワーク アドレスに対して求められます。 ネットワーク アドレスが使用されます。 サブネットです。たとえば、192.191.190.0 です。 すべてのプロンプトで、既定値をそのまま使用したり、必要に応じて変更できます。
   
3. 次に、ディスク ベースのフェンス操作は、SBD を構成するかどうかを求められます。 この構成は、必要な場合は、後で行うことができます。 SBD でない場合は、構成とは異なり RHEL および Ubuntu、`stonith-enabled`は既定で false に設定します。
   
4. 最後に、管理用 IP アドレスを構成するかどうかを求められます。 この IP アドレスは省略可能では、関数を使用して HA Web Konsole (HAWK) に接続するために使用するクラスターの IP アドレスを作成するという意味での Windows Server フェールオーバー クラスター (WSFC) の IP アドレスに似ています。 でも、この構成では省略可能です。
   
5. クラスターが稼働して発行することによって 
   ```bash
   sudo crm status
   ```
   
6. 変更、 *hacluster*とパスワード 
   ```bash
   sudo passwd hacluster
   ```
   
7. 管理用の IP アドレスを構成した場合ものパスワードの変更をテストするブラウザーでテストできます*hacluster*します。
   ![](./media/sql-server-linux-deploy-pacemaker-cluster/image2.png)
   
8. クラスターのノードとなる別の SLES サーバーで実行します。 
   ```bash
   sudo ha-cluster-join
   ```
   
9. メッセージが表示されたら、名前または前の手順でクラスターの最初のノードとして構成されたサーバーの IP アドレスを入力します。 サーバーは、既存のクラスターにノードとして追加されます。
   
10. 発行することによって、ノードが追加されたことを確認します。 
   ```bash
   sudo crm status
   ```
   
11. 変更、 *hacluster*とパスワード 
   ```bash
   sudo passwd hacluster
   ```
   
12. 手順 8-11 の他のすべてのサーバー クラスターに追加するには

## <a name="install-the-sql-server-ha-and-sql-server-agent-packages"></a>SQL Server の HA および SQL Server エージェントのパッケージをインストールします。
次のコマンドを使用して、SQL Server の HA パッケージをインストールして[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]エージェント、既にインストールされていない場合。 インストールした後、HA パッケージをインストールする[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]の再起動が必要[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]用にも使用します。 これらの手順は、マイクロソフトのパッケージのリポジトリが既に設定されている、ため前提としています。[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]この時点でインストールする必要があります。
> [!NOTE]
> - 使用しない場合[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]ログ配布やその他の使用はすべてのエージェントがないためパッケージ化、インストール*mssql server エージェント*をスキップできます。
> - その他のオプションのパッケージの[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]linux では、 [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] 、フルテキスト検索 (*mssql-サーバー-fts*) と[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Integration Services (*mssql server は*)、いません。FCI または AG のいずれかの高可用性のために必要です。

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

## <a name="next-steps"></a>次のステップ

このチュートリアルでは、SQL Server on Linux の Pacemaker クラスターをデプロイする方法について説明しました。 学習したします。
> [!div class="checklist"]
> * 高可用性アドオンをインストールし、Pacemaker をインストールします。
> * Pacemaker (RHEL および Ubuntu のみ) 用のノードを準備します。
> * Pacemaker クラスターを作成します。
> * SQL Server の HA および SQL Server エージェントのパッケージをインストールします。

作成して、SQL Server on Linux の可用性グループの構成を参照してください。

> [!div class="nextstepaction"]
> [作成し、SQL Server on Linux の可用性グループの構成](sql-server-linux-create-availability-group.md)します。

