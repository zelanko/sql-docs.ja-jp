---
title: SQL Server on Docker での分散トランザクションを使用する方法
description: この記事では、Linux 上の MSDTC を構成するため Dprovides チュートリアルを使用する方法について説明します。
author: VanMSFT
ms.author: vanto
manager: jroth
ms.date: 09/25/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 808f9d0ef2911aa79c8a4fc5af55a222a056004b
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67834046"
---
# <a name="how-to-use-distributed-transactions-with-sql-server-on-docker"></a>SQL Server on Docker での分散トランザクションを使用する方法

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、分散トランザクションの Docker で SQL Server Linux コンテナーを設定する方法について説明します。

SQL Server 2019 プレビュー以降は、コンテナー イメージは、Microsoft 分散トランザクション コーディネーター (MSDTC) 分散トランザクションに必要なをサポートします。 MSDTC の通信要件を理解するのを参照してください。 [Linux で Microsoft 分散トランザクション コーディネーター (MSDTC) を構成する方法](sql-server-linux-configure-msdtc.md)します。 この記事では、特別な要件と SQL Server の Docker コンテナーに関連するシナリオについて説明します。

## <a name="configuration"></a>構成

Docker のコンテナーでの MSDTC トランザクションを有効にするには、2 つの新しい環境変数を設定する必要があります。

- **MSSQL_RPC_PORT**: RPC エンドポイント マッパー サービスにバインドし、リッスンする TCP ポート。  
- **MSSQL_DTC_TCP_PORT**: ポート MSDTC サービスがリッスンするように構成されていること。

### <a name="pull-and-run"></a>プルし、実行

次の例では、これらの環境変数を使用してプルし、MSDTC 用に構成された 1 つの SQL Server コンテナーを実行する方法を示します。 これにより、すべてのホスト上のアプリケーションと通信することができます。

```bash
docker run \
   -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
   -e 'MSSQL_RPC_PORT=135' -e 'MSSQL_DTC_TCP_PORT=51000' \
   -p 51433:1433 -p 135:135 -p 51000:51000  \
   -d mcr.microsoft.com/mssql/server:2019-CTP3.1-ubuntu
```

> [!IMPORTANT]
> 前のコマンドでは、Linux で実行されている Docker がのみ機能します。 Windows 上の Docker での Windows ホストは、既にポート 135 でリッスンします。 削除することができます、`-p 135:135`が、Windows 上の Docker のパラメーターがいくつかの制限。 結果のコンテナーは、使用できませんはホストに関連する分散トランザクションホスト上の docker コンテナー間で分散トランザクションにのみ参加できます。

このコマンドで、 **RPC エンドポイント マッパー**ポート 135、サービスにバインドし、 **MSDTC**サービスがポート 51000 docker 仮想ネットワーク内にバインドされました。 Docker の仮想ネットワーク内でポート 1433 で SQL Server の TDS 通信が行われます。 これらのポートが外部で公開されているホストに TDS ポート 51433、RPC エンドポイント マッパー ポート 135、および MSDTC ポート 51000 として。

> [!NOTE]
> RPC エンドポイント マッパーと MSDTC ポート、ホストとコンテナーで同じである必要ありません。 コンテナーに対する 135 を使用する RPC エンドポイント マッパーのポートが構成されたときに、13501 またはその他の使用可能なポート、ホスト サーバー上のポートにマップ可能性がある可能性があります。

## <a name="configure-the-firewall"></a>ファイアウォールの構成

ホストを経由して、通信するためにも、コンテナーのホスト サーバー上にファイアウォールを構成する必要があります。 開いているすべてのファイアウォール ポートを docker コンテナーは、外部の通信は公開します。 前の例では、ポート 135、51433、および 51000 になります。 これらは、ホスト自体にポートと、コンテナー内にマップするポートです。 そのため、51001、ホストのポートにマップされていたコンテナーのマッパー ポート 51000 RPC エンドポイントが、ポート ホストとの通信のためのファイアウォールで 51001 (51000 されません) を開始する必要があります。  

次の例では、Ubuntu 上でこれらの規則を作成する方法を示します。

```bash
sudo ufw allow from any to any port 51433 proto tcp
sudo ufw allow from any to any port 51000 proto tcp
sudo ufw allow from any to any port 135 proto tcp
```

次の例では、どのように実行できる Red Hat Enterprise Linux (RHEL) では示しています。

```bash
sudo firewall-cmd --zone=public --add-port=51999/tcp --permanent
sudo firewall-cmd --zone=public --add-port=51433/tcp --permanent
sudo firewall-cmd --zone=public --add-port=135/tcp --permanent
sudo firewall-cmd --reload
```

## <a name="configure-port-routing-on-the-host"></a>ポートがホストでルーティングを構成します。

前の例では、1 つの Docker コンテナーでは、RPC ポート 135 をホストのポート 135 にマップされるため、ホストでの分散トランザクションは必要があります構成なしで動作ようになりました。 ある直接ポート 135、コンテナーを使用する SQL Server がコンテナーに昇格した特権で実行されるため、注意してください。 コンテナーの外部での SQL server の別のエフェメラル ポートを使用する必要があり、ポート 135 へのトラフィックをそのポートにルーティングする必要があります。

ただし、コンテナーのポート 135 を 13500 など、ホスト上の別のポートにマップした場合は、し構成する必要ポートがホストにルーティングします。 これにより、docker コンテナーのホストおよびその他の外部のサーバーと分散トランザクションに参加できます。 詳細については、次を参照してください。[ポート ルーティングを構成する](sql-server-linux-configure-msdtc.md#configure-port-routing)します。

## <a name="next-steps"></a>次のステップ

Linux 上の MSDTC に関する詳細については、次を参照してください。 [Linux で Microsoft 分散トランザクション コーディネーター (MSDTC) を構成する方法](sql-server-linux-configure-msdtc.md)します。
