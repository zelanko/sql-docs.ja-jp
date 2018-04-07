---
title: 高可用性、災害復旧の Microsoft Drivers for PHP for SQL Server のサポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 04/04/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 73a80821-d345-4fea-b076-f4aabeb4af3e
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6cb7f145f14861720d11401a3d60db0ce0efcfd9
ms.sourcegitcommit: 094c46e7fa6de44735ed0040c65a40ec3d951b75
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="support-for-high-availability-disaster-recovery"></a>高可用性、障害復旧のサポート
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このトピックについて説明[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]サポート (version 3.0 で追加) 高可用性、災害復旧--[!INCLUDE[ssHADR](../../includes/sshadr_md.md)]です。  [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]は [!INCLUDE[ssSQL11](../../includes/sssql11_md.md)] で新たにサポートされました。 [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]の詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] オンライン ブックを参照してください。  
  
Version 3.0 で、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]の可用性グループ リスナーを指定することができます (高可用性、災害復旧) 接続プロパティの可用性グループ (AG)。 場合、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]アプリケーションがフェールオーバーが発生した AlwaysOn データベースに接続している、元の接続が切断され、アプリケーションは、フェールオーバー後の作業を続行する新しい接続を開く必要があります。  
  
複数の IP アドレスは、ホスト名に関連付けられていて、可用性グループ リスナーに接続していない場合、 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] DNS エントリに関連付けられているすべての IP アドレスを順番に反復処理されます。 DNS サーバーが最初に返した IP アドレスがネットワーク インターフェイス カード (NIC) にバインドされていない場合、この処理に時間がかかる可能性があります。 可用性グループ リスナーに接続するとき、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]を並行して、接続試行はすべての IP アドレスへの接続を確立する試行が成功すると、ドライバーは保留中の接続の試行で破棄されます。  
  
> [!NOTE]  
> 接続タイムアウト値を大きくし、接続再試行ロジックを実装することにより、アプリケーションが可用性グループに接続する確立が高まります。 また、可用性グループのフェールオーバーにより接続が失敗する可能性があるため、接続再試行ロジックを実装して、再接続されるまで、失敗した接続の再接続を試行する必要があります。  
  
## <a name="connecting-with-multisubnetfailover"></a>MultiSubnetFailover を使用した接続  
**MultiSubnetFailover**接続プロパティは、可用性グループまたはフェールオーバー クラスター インスタンスで、アプリケーションが展開されていることを示します、 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] プライマリ上のデータベースに接続しようとして、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]すべての ip アドレスに接続しようとしてのインスタンスに対応します。 ときに**MultiSubnetFailover = true**が指定されている接続の場合、クライアントは、オペレーティング システムの既定の TCP 再転送間隔よりも高速接続試行を再試行します。 これにより、AlwaysOn 可用性グループまたは AlwaysOn フェールオーバー クラスター インスタンスのフェールオーバー後、再接続されるまでの時間を短縮することができます。単一サブネットとマルチサブネットの可用性グループ インスタンスおよびフェールオーバー クラスター インスタンスに適用することができます。  
  
常に指定**MultiSubnetFailover = True** SQL Server 2012 可用性グループ リスナーまたは SQL Server 2012 フェールオーバー クラスター インスタンスに接続するときにします。 **MultiSubnetFailover**すべての可用性グループと SQL Server 2012 フェールオーバー クラスター インスタンスに対して高速フェールオーバーを有効にし、単一サブネットおよびマルチ サブネットの AlwaysOn トポロジにおけるフェールオーバー時間を大幅に削減します。 マルチサブネット フェールオーバーの際には、クライアントは複数の接続を並列で試行します。 サブネットのフェールオーバー中に、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]は積極的に TCP 接続を再試行します。  
  
接続文字列キーワードの詳細については[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]を参照してください[接続オプション](../../connect/php/connection-options.md)です。  
  
指定する**MultiSubnetFailover = true**可用性グループ リスナーまたはフェールオーバー クラスター インスタンス以外のものへの接続は負の値のパフォーマンスに影響されない可能性があり、サポートされていません。  
  
可用性グループ内のサーバーに接続する際には、次のガイドラインに従います。  
  
-   単一サブネットまたはマルチサブネットに接続する場合に **MultiSubnetFailover** 接続プロパティを使用すると、パフォーマンスを向上させることができます。  
  
-   可用性グループに接続するには、接続文字列でサーバーとして、可用性グループの可用性グループ リスナーを指定します。  
  
-   64 個を超える数の IP アドレスが構成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] インスタンスに接続すると、接続エラーが発生します。  
  
-   **MultiSubnetFailover** 接続プロパティを使用するアプリケーションの動作は、認証の種類 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 認証、Kerberos 認証、または Windows 認証) の影響を受けません。  
  
-   値を大きく**loginTimeout**フェールオーバー時間に対応し、アプリケーションの接続再試行回数を削減します。  
  
-   分散トランザクションはサポートされていません。  
  
読み取り専用のルーティングが無効である場合、次の状況では可用性グループのセカンダリ レプリカの場所には接続できません。  
  
1.  セカンダリ レプリカの場所が、接続を許可するように構成されていない。  
  
2.  アプリケーションに **ApplicationIntent=ReadWrite** (後述します) が使用されているが、セカンダリ レプリカの場所が読み取り専用アクセスとして構成されている。  
  
プライマリ レプリカが読み取り専用ワークロードを拒否するように構成されているとき、接続文字列に **ApplicationIntent=ReadOnly** が含まれていると、接続は失敗します。  
  
## <a name="upgrading-to-use-multi-subnet-clusters-from-database-mirroring"></a>データベース ミラーリングの使用からマルチサブネット クラスターの使用へのアップグレード  
接続文字列に **MultiSubnetFailover** および **Failover_Partner** の接続キーワードが存在する場合、接続エラーが発生します。 また、**MultiSubnetFailover** が使用されているとき、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] から、データベース ミラーリング ペアに属していることを示すフェールオーバー パートナー応答が返された場合にも、エラーが発生します。  
  
アップグレードする場合、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]アプリケーション現在データベース ミラーリングを使用して、マルチ サブネットのシナリオでは、削除する必要あります、 **Failover_Partner**接続プロパティと、コードに置き換えます**MultiSubnetFailover** 'éý'**はい**し、接続文字列でサーバー名を可用性グループ リスナーに置き換えます。 接続文字列で使用する場合**Failover_Partner**と**MultiSubnetFailover = true**ドライバーでエラーが発生します。 ただし、接続文字列で使用する場合**Failover_Partner**と**MultiSubnetFailover = false** (または**ApplicationIntent = ReadWrite**)、アプリケーション データベースが使用されますミラー化できます。  
  
ドライバーが場合と、AG のプライマリ データベースでデータベース ミラーリングを使用する場合に、エラーが返されます**MultiSubnetFailover = true**は可用性グループにはなく、プライマリ データベースに接続する接続文字列で使用リスナー。  


[!INCLUDE[specify-application-intent_read-only-routing](~/includes/paragraph-content/specify-application-intent-read-only-routing.md)]


## <a name="see-also"></a>参照  
[サーバーへの接続](../../connect/php/connecting-to-the-server.md)  
  
