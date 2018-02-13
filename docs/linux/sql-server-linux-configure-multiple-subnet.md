---
title: "Linux 上の複数のサブネット Always On 可用性グループおよびフェールオーバー クラスター インスタンスの構成 |Microsoft ドキュメント"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 12/1/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.workload: On Demand
ms.openlocfilehash: 84195d2451664b2bee81ebbb1dc3b7d9d89060d5
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2018
---
# <a name="configure-multiple-subnet-always-on-availability-groups-and-failover-cluster-instances"></a>複数のサブネット Always On 可用性グループおよびフェールオーバー クラスター インスタンスを構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

ときに常に 可用性グループ (AG) またはフェールオーバー クラスター インスタンス (FCI) にまたがる複数のサイト、サイトの各通常、独自のネットワークがあります。 多くの場合、つまり、各サイトが独自の IP アドレス指定します。 たとえば、サイト A のアドレスが 192.168.1 で開始します。*x*し 192.168.2 とサイト B のアドレスを開始します*。x*ここで、 *x*サーバーに一意の IP アドレスの一部です。 何らかのネットワーク レイヤーでの場所にルーティングせずと、これらのサーバーは互いに通信することができません。 このシナリオを処理する 2 つの方法: 結びます。 また、2 つの異なるサブネット、VLAN と呼ばれる、ネットワーク設定、または、サブネット間のルーティングを構成します。

## <a name="vlan-based-solution"></a>VLAN ベースのソリューション
 
**前提条件となる**: ため、VLAN ベースのソリューションでは、可用性グループまたは FCI に参加する各サーバーようにが必要 2 つのネットワーク カード (Nic) (デュアル ポート NIC は、1 つの物理サーバーに障害点になります) 適切な可用性のために割り当てることができる IP アドレスでネイティブのサブネットだけでなく、VLAN のいずれか。 これは、独自のネットワークにも必要のある iSCSI などその他のネットワーク要件に加えします。

可用性グループまたは FCI の IP アドレスの作成は、VLAN で行われます。 次の例では、VLAN は 192.168.3 のサブネットがします。*x*のため、可用性グループまたは FCI 用に作成された IP アドレスは 192.168.3.104 します。 可用性グループまたは FCI に割り当てられている単一の IP アドレスがあるため、構成詳細 nothing 必要があります。

![](./media/sql-server-linux-configure-multiple-subnet/image1.png)

## <a name="configuration-with-pacemaker"></a>ペースの構成

世界では、Windows、Windows Server フェールオーバー クラスター (WSFC) はネイティブに複数のサブネットをサポートし、IP アドレスに、OR 依存関係を使用して複数の IP アドレスを処理します。 Linux では、OR 依存関係はありませんが、方法は、ペースでネイティブに適切なマルチ サブネットを実現するために、次に示すようにします。 これは、単にリソースを変更する通常のペースのコマンドラインを使用して行うことはできません。 クラスター情報ベース (CIB) を変更する必要があります。 CIB は、ペースの構成で XML ファイルです。

![](./media/sql-server-linux-configure-multiple-subnet/image2.png)

### <a name="update-the-cib"></a>更新プログラム、CIB

1.  CIB をエクスポートします。

    **Red Hat Enterprise Linux (RHEL) および Ubuntu**

    ```bash
    sudo pcs cluster cib <filename>
    ```

    **SUSE Linux Enterprise Server (SLES)**

    ```bash
    sudo cibadmin -Q > <filename>
    ```

    ここで*filename* CIB を呼び出したい名前を指定します。

2.  生成されたファイルを編集します。 探して、`<resources>`セクションです。 可用性グループまたは FCI に対して作成されたさまざまなリソースが表示されます。 IP アドレスに関連付けられている 1 つを検索します。 追加、`<instance attributes>`上または既存のものでは、下の 2 番目の IP アドレスの情報とその前にセクション`<operations>`です。 次の構文に似ています。

    ```xml
    <instance attributes id="<NameForAttribute>" score="<Score>">
        <rule id="<RuleName>" score="INFINITY">
            <expression id="<ExpressionName>" attribute="\#uname" operation="eq" value="<NodeNameInSubnet2>" />
        </rule>
        <nvpair id="<NameForSecondIP>" name="ip" value="<IPAddress>"/>
        <nvpair id="<NameForSecondIPNetmask>" name="cidr\_netmask" value="<Netmask>"/>
    </instance attributes>
    ```
    
    ここで*NameForAttribute*この属性の一意の名前は、*スコア*プライマリ サブネットのより大きい必要があります、属性に割り当てられた番号*RuleName*、ルールの名前を指定*ExpressionName* 、式の名前は、 *NodeNameInSubnet2* 、他のサブネット内のノードの名前を指定*NameForSecondIP* 2 番目の IP アドレスに関連付けられている名前を指定します*IPAddress* 2 番目のサブネットの IP アドレスは、 *NameForSecondIPNetmask*ネットマスクに関連付けられている名前を指定し、*ネットマスク*は、2 番目のサブネットのネットマスク。
    
    例を次に示します。
    
    ```xml
    <instance attributes id="Node3-2nd-IP" score="2">
        <rule id="Subnet2-IP" score="INFINITY">
            <expression id="Subnet2-Node" attribute="\#uname" operation="eq" value="Node3" />
        </rule>
        <nvpair id="IP-In-Subnet-2" name="ip" value="192.168.2.102"/>
        <nvpair id="Netmask-For-IP2" name="cidr\_netmask" value="24" />
    </instance attributes>
    ```

3.  変更された CIB をインポートし、ペースを再構成します。

    **RHEL/Ubuntu**
    
    ```bash
    sudo pcs cluster cib-push <filename>
    ```

    **SLES**
    
    ```bash
    sudo cibadmin -R -x <filename>
    ```

    ここで*filename* IP アドレス情報が変更された CIB ファイルの名前を指定します。

### <a name="check-and-verify-failover"></a>確認し、フェールオーバーの確認

1.  適用した後、CIB が正常に更新された構成と、ペースで IP アドレス リソースに関連付けられた DNS 名に対して ping を実行します。 これにより、AG または FCI をホストしているサブネットに関連付けられている IP アドレスが反映されます。
2.  可用性グループまたは FCI を他のサブネットに失敗します。
3.  可用性グループまたは FCI が完全にオンライン後は、IP アドレスに関連付けられた DNS 名を ping します。 これにより、2 番目のサブネットの IP アドレスが反映されます。
4.  必要な場合、可用性グループまたは FCI を元のサブネットに失敗します。
