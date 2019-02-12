---
title: Linux 上の複数のサブネット Always On 可用性グループおよびフェールオーバー クラスター インスタンスの構成 |Microsoft Docs
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 12/01/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 4d142c1b97d6e0643a44c200db032babbef30412
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56020553"
---
# <a name="configure-multiple-subnet-always-on-availability-groups-and-failover-cluster-instances"></a>複数のサブネット Always On 可用性グループおよびフェールオーバー クラスター インスタンスを構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Always On 可用性グループ (AG で) またはフェールオーバー クラスター インスタンス (FCI) にまたがる場合は、複数のサイトの各サイトは、通常が、独自のネットワークです。 多くの場合、つまり、各サイトでは、独自の IP アドレス指定します。 たとえば、サイト A のアドレスは 192. 168.1 で開始します。*x* 192.168.2 始めるサイト B のアドレス *。x*ここで、 *x*は、サーバーに一意の IP アドレスの一部です。 ネットワーク レイヤーでルーティングを使わず、これらのサーバーは互いに通信できません。 このシナリオを処理する 2 つの方法はあります。 2 つの異なるサブネット、VLAN と呼ばれるブリッジ ネットワークをセットアップまたは、サブネット間のルーティングを構成します。

## <a name="vlan-based-solution"></a>VLAN ベースのソリューション
 
**前提条件となる**:VLAN ベースのソリューションでは、各サーバー、AG または FCI に参加している必要があります (デュアル ポート NIC は、1 つの物理サーバーに障害点になります) 適切な可用性のための 2 つのネットワーク カード (Nic)、ネイティブのサブネットと 1 つ上の IP アドレスが割り当てられますことができます。VLAN です。 これは、iSCSI も、独自のネットワークを必要とするなどの他のネットワーク ニーズです。

AG または FCI の IP アドレスの作成は、VLAN で行われます。 次の例では、VLAN は 192.168.3 のサブネットが。*x*ので、AG または FCI 用に作成された IP アドレスは 192.168.3.104 します。 何も追加は、AG または FCI に割り当てられている単一の IP アドレスがあるため、構成する必要があります。

![](./media/sql-server-linux-configure-multiple-subnet/image1.png)

## <a name="configuration-with-pacemaker"></a>Pacemaker と構成

Windows の世界で Windows Server フェールオーバー クラスター (WSFC) はネイティブ複数のサブネットをサポートし、IP アドレスで、OR 依存関係を使用して複数の IP アドレスを処理します。 Linux では、OR 依存関係はありませんが、次に示すように、Pacemaker でネイティブに適切なマルチ サブネットを実現する方法があります。 これは、単にリソースを変更する通常の Pacemaker のコマンドラインを使用して行うことはできません。 クラスター情報ベース (CIB) を変更する必要があります。 CIB は、Pacemaker 構成 XML ファイルです。

![](./media/sql-server-linux-configure-multiple-subnet/image2.png)

### <a name="update-the-cib"></a>CIB を更新します。

1.  CIB をエクスポートします。

    **Red Hat Enterprise Linux (RHEL) および Ubuntu**

    ```bash
    sudo pcs cluster cib <filename>
    ```

    **SUSE Linux Enterprise Server (SLES)**

    ```bash
    sudo cibadmin -Q > <filename>
    ```

    場所*filename* CIB を呼び出そうとする名前を指定します。

2.  生成されたファイルを編集します。 探して、`<resources>`セクション。 AG または FCI に対して作成されたさまざまなリソースが表示されます。 関連付けられた IP アドレスを見つけます。 追加、`<instance attributes>`上または既存のものでは、下の 2 つ目の IP アドレスの情報を使用する前にセクション`<operations>`します。 次の構文に似ています。

    ```xml
    <instance attributes id="<NameForAttribute>" score="<Score>">
        <rule id="<RuleName>" score="INFINITY">
            <expression id="<ExpressionName>" attribute="\#uname" operation="eq" value="<NodeNameInSubnet2>" />
        </rule>
        <nvpair id="<NameForSecondIP>" name="ip" value="<IPAddress>"/>
        <nvpair id="<NameForSecondIPNetmask>" name="cidr\_netmask" value="<Netmask>"/>
    </instance attributes>
    ```
    
    場所*NameForAttribute* 、この属性の一意の名前は、*スコア*プライマリ サブネットのより大きい必要があります、属性に割り当てられた番号*RuleName*、ルールの名前を指定*ExpressionName* 、式の名前は、 *NodeNameInSubnet2* 、他のサブネット内のノードの名前を指定します*NameForSecondIP* 2 番目の IP アドレスに関連付けられた名前を指定します*IPAddress* 2 番目のサブネットの IP アドレスは、 *NameForSecondIPNetmask*ネットマスクに関連付けられている名前を指定します、*ネットマスク*が 2 番目のサブネットのネットマスク。
    
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

3.  変更された CIB をインポートし、Pacemaker を再構成します。

    **RHEL/Ubuntu**
    
    ```bash
    sudo pcs cluster cib-push <filename>
    ```

    **SLES**
    
    ```bash
    sudo cibadmin -R -x <filename>
    ```

    場所*filename* CIB ファイルに変更された IP アドレス情報の名前を指定します。

### <a name="check-and-verify-failover"></a>フェールオーバーを確認し、

1.  CIB が更新された構成と正常に適用されると、Pacemaker で IP アドレス リソースに関連付けられた DNS 名に対して ping を実行します。 現在、AG または FCI をホストするサブネットに関連付けられている IP アドレスを反映したものにする必要があります。
2.  AG または FCI を他のサブネットに失敗します。
3.  AG または FCI が完全にオンライン、IP アドレスに関連付けられた DNS 名に対して ping を実行します。 2 つ目のサブネットの IP アドレスを反映したものにする必要があります。
4.  必要な場合、AG または FCI を元のサブネットに失敗します。
