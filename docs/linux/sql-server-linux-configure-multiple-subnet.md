---
title: 複数サブネットの可用性グループと FCI の構成 (Linux)
description: 複数サブネットの Always On 可用性グループとフェールオーバー クラスター インスタンス (FCI) を SQL Server on Linux に構成する方法について説明します。
ms.custom: seo-lt-2019
author: liweiSecurity
ms.author: liweiyin
ms.reviewer: VanMSFT
ms.date: 07/28/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 5abe1d99f753e0f41ca74a0864079293800dc1df
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87362977"
---
# <a name="configure-multiple-subnet-always-on-availability-groups-and-failover-cluster-instances"></a>複数サブネットの Always On 可用性グループとフェールオーバー クラスター インスタンスを構成する

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

Always On 可用性グループ (AG) またはフェールオーバー クラスター インスタンス (FCI) が複数のサイトにまたがっている場合、通常、各サイトには独自のネットワークがあります。 つまり、多くの場合、各サイトに独自の IP アドレス指定があります。 たとえば、サイト A のアドレスが 192.168.1.*x* から開始し、サイト B のアドレスが 192.168.2.*x* から開始します (*x* はサーバー固有の IP アドレスの一部)。 ネットワーク層で何らかのルーティングが行われていない場合、これらのサーバーは相互に通信できません。 このシナリオに対処する方法は 2 つあります。2 つの異なるサブネットをブリッジするネットワーク (VLAN) をセットアップするか、サブネット間のルーティングを構成します。

## <a name="vlan-based-solution"></a>VLAN ベースのソリューション
 
**前提条件**:VLAN ベースのソリューションの場合、適切な可用性を確保するには、AG または FCI に参加する各サーバーに 2 枚のネットワーク カード (NIC) が必要です (デュアル ポート NIC は物理サーバー上の単一障害点になります)。これにより、IP アドレスをネイティブ サブネットだけでなく、VLAN 上のサブネットにも割り当てられるようになります。 これに加えて、他のネットワーク ニーズもあります (同じく独自のネットワークを必要とする iSCSI など)。

AG または FCI 用の IP アドレスの作成は、VLAN で実行されます。 次の例では、VLAN のサブネットは 192.168.3.*x* であるため、AG または FCI に作成される IP アドレスは 192.168.3.104 です。 1 つの IP アドレスが AG または FCI に割り当てられているため、その他の構成は必要ありません。

![複数のサブネットを構成する 01](./media/sql-server-linux-configure-multiple-subnet/image1.png)

## <a name="configuration-with-pacemaker"></a>Pacemaker を使用した構成

Windows の世界では、Windows Server フェールオーバー クラスター (WSFC) が複数のサブネットをネイティブでサポートし、IP アドレスに対して OR 依存関係を使用して複数の IP アドレスを処理します。 Linux には OR 依存関係はありませんが、次に示すように、適切な複数のサブネットを Pacemaker でネイティブに実現する方法があります。 通常の Pacemaker コマンドラインを使用してリソースを変更しただけでは、これを行うことはできません。 クラスター情報ベース (CIB) を変更する必要があります。 CIB は、Pacemaker 構成の XML ファイルです。

![複数のサブネットを構成する 02](./media/sql-server-linux-configure-multiple-subnet/image2.png)

### <a name="update-the-cib"></a>CIB を更新する

1. CIB をエクスポートします。

    **Red Hat Enterprise Linux (RHEL) と Ubuntu**

    ```bash
    sudo pcs cluster cib <filename>
    ```

    **SUSE Linux Enterprise Server (SLES)**

    ```bash
    sudo cibadmin -Q > <filename>
    ```

    ここで、*filename* は CIB に付ける名前です。

2. 生成されたファイルを編集します。 `<resources>` セクションを探します。 AG または FCI に対して作成されたさまざまなリソースが表示されます。 IP アドレスに関連付けられたものを探します。 2 番目の IP アドレスの情報を含む `<instance attributes>` セクションを、既存のセクションの前後いずれか、ただし `<operations>` の前に追加します。 構文は次のようになります。

    ```xml
    <instance attributes id="<NameForAttribute>">
        <nvpair id="<NameForIP>" name="ip" value="<IPAddress>"/>
    </instance attributes>
    ```
    
    *NameForAttribute* はこの属性の一意の名前、*NameForIP* は IP アドレスに関連付けられている名前、*IPAddress* は 2 つ目のサブネットの IP アドレスです。
    
    次に例を示します。
    
    ```xml
    <instance attributes id="virtualip-instance_attributes">
        <nvpair id="virtualip-instance_attributes-ip" name="ip" value="192.168.1.102"/>
    </instance attributes>
    ```
    
    既定では、エクスポートされた CIB XML ファイルには <instance/> が 1 つだけあります。 2 つのサブネットがあるとします。<instance/> エントリが 2 つ必要です。
    2 つのサブネットのエントリの例を次に示します。
    
    ```xml
    <instance attributes id="virtualip-instance_attributes1">
        <rule id="Subnet1-IP" score="INFINITY" boolean-op="or">
            <expression id="Subnet1-Node1" attribute="#uname" operation="eq" value="Node1" />
            <expression id="Subnet1-Node2" attribute="#uname" operation="eq" value="Node2" />
        </rule>
        <nvpair id="IP-In-Subnet1" name="ip" value="192.168.1.102"/>
    </instance attributes>
    <instance attributes id="virtualip-instance_attributes2">
        <rule id="Subnet2-IP" score="INFINITY">
            <expression id="Subnet2-Node1" attribute="#uname" operation="eq" value="Node3" />
        </rule>
        <nvpair id="IP-In-Subnet2" name="ip" value="192.168.2.102"/>
    </instance attributes>
    ```
   
   "boolean-op="or"" は、サブネットに複数のサーバーがあるときに使用されます。


3. 変更した CIB をインポートし、Pacemaker を再構成します。

    **RHEL/Ubuntu**
    
    ```bash
    sudo pcs cluster cib-push <filename>
    ```

    **SLES**
    
    ```bash
    sudo cibadmin -R -x <filename>
    ```

    ここで、*filename* は 変更した IP アドレス情報を含む CIB ファイルの名前です。

### <a name="check-and-verify-failover"></a>フェールオーバーを確認して検証する

1. CIB が更新済みの構成に正常に適用されたら、Pacemaker で IP アドレス リソースに関連付けられている DNS 名に対して ping を実行します。 これは、現在 AG または FCI をホストしているサブネットに関連付けられた IP アドレスを反映する必要があります。

2. AG または FCI を他のサブネットにフェールオーバーします。

3. AG または FCI が完全にオンラインになったら、IP アドレスに関連付けられている DNS 名に対して ping を実行します。 これは、2 番目のサブネットの IP アドレスを反映する必要があります。

4. 必要であれば、AG または FCI を元のサブネットにフェールオーバーします。

次の CSS 投稿では、3 つのサブネットに CIB を構成する方法を確認できます。詳細については、「[CIB を変更し、複数サブネット AlwaysOn 可用性グループを構成する](https://techcommunity.microsoft.com/t5/sql-server-support/configure-multiple-subnet-alwayson-availability-groups-by/ba-p/1544838)」を参照してください。
