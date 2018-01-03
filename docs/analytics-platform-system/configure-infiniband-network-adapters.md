---
title: "Analytics Platform System (APS) の InfiniBand ネットワーク アダプターを構成します。"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.suite: sql
ms.custom: 
ms.technology: mpp-data-warehouse
description: "管理 ノード SQL Server 並列データ ウェアハウス (PDW) に接続する非アプライアンス クライアント サーバーの InfiniBand ネットワーク アダプターを構成する方法について説明します。"
ms.date: 01/05/2017
ms.topic: article
ms.assetid: 61f3c51a-4411-4fe8-8b03-c8e1ba279646
caps.latest.revision: "15"
ms.openlocfilehash: 052dfcb32de7fb84acc0ce97c55775944a1d0dc1
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="configure-infiniband-network-adapters-for-analytics-platform-system"></a>Analytics Platform System の InfiniBand ネットワーク アダプターを構成します。
管理 ノード SQL Server 並列データ ウェアハウス (PDW) に接続する非アプライアンス クライアント サーバーの InfiniBand ネットワーク アダプターを構成する方法について説明します。 読み込み、バックアップ、およびその他のプロセスがアクティブの InfiniBand ネットワークに自動的に接続できるように基本的な接続と高可用性は、これらの手順に従います。  
  
## <a name="Basics"></a>説明  
これらの手順では、検索し、し、正しい InfiniBand IP アドレスとサブネット マスク、サーバーで設定 InfiniBand 接続する方法を示します。 APS アプライアンス DNS を使用して、接続がアクティブの InfiniBand ネットワークに解決されるようにするようにサーバーを設定する方法についても説明します。  
  
高可用性を実現 AP は、2 つの InfiniBand ネットワーク、1 つはアクティブとパッシブの 1 つです。 各 InfiniBand ネットワークには、コントロールのノードに対して異なる IP アドレスがあります。 アクティブの InfiniBand ネットワークに障害が発生した場合は、アクティブなネットワークがパッシブの InfiniBand ネットワークになります。 このような場合、スクリプトまたはプロセスに自動的に接続アクティブの InfiniBand ネットワーク スクリプトのパラメーターを変更することがなくです。  
  
具体的には、このトピックでは説明します。  
  
1.  APS DNS の InfiniBand IP アドレスにサーバーを検索 (appliance_domain AD01 と appliance_domain *-AD02)。 これを行うには、AD01 および AD02 のサーバーにログインし、各 InfiniBand ネットワークの IP アドレスを取得します。 AD ノード上の InfiniBand IP アドレスは、DNS の IP アドレスです。  
  
2.  APS の InfiniBand ネットワークで使用可能な IP アドレスを使用するには、各ネットワーク アダプターを構成します。  
  
    1.  呼ばれる TeamIB1、および使用可能な IP アドレスとその他のアダプターと呼ばれる 2 番目の InfiniBand ネットワークの最初の InfiniBand ネットワークの使用可能な IP アドレスを 1 つのアダプターを構成する場合は 2 つの InfiniBand ネットワーク アダプターがある場合は、TeamIB2 です。 優先 DNS サーバーおよび appliance_domain AD02 TeamIB1 として IP アドレスを使う appliance_domain AD01 TeamIB1 TeamIB1 ネットワーク アダプターの代替 DNS サーバーに IP アドレス。 優先 DNS サーバーおよび appliance_domain AD02 TeamIB2 として IP アドレスを使う appliance_domain AD01 TeamIB2 TeamIB2 のネットワーク アダプターの代替 DNS サーバーに IP アドレス。  
  
    2.  1 つだけの InfiniBand ネットワーク アダプターがあれば、InfiniBand ネットワークのいずれかから使用可能な IP アドレスとアダプターを構成します。 Appliance_domain AD01 TeamIB1 および appliance_domain AD02 TeamIB1 のいずれかを使用してまたは appliance_domain AD01 TeamIB2 および appliance_domain AD02 TeamIB2 の方を使用して、このアダプターで、優先および代替 DNS サーバーを構成するが、同じネットワークに、優先として構成されているアダプターと代替の DNS サーバーそれぞれします。  
  
3.  作業中の InfiniBand ネットワークに接続を解決するのには APS DNS サーバーを使用する InfiniBand ネットワーク アダプターを構成します。  
  
    1.  これを構成するのにには、クライアント サーバー上の DNS サフィックスの一覧の先頭にアプライアンス ドメインの DNS サフィックスを追加するのに TCP/IP 詳細設定を使用するされます。 これは、のみ; のネットワーク アダプターのいずれかで構成する必要があります。この設定は、両方のアダプターに適用されます。  
  
InfiniBand ネットワーク アダプターを構成すると、クライアント プロセスに接続できる InfiniBand ネットワーク上の管理ノードを使用して`PDW_region-SQLCTL01`サーバーのアドレスに対応します。 サーバーは、分析プラットフォーム システム DNS サフィックスを追加または完全なアドレスを入力する`PDW_region-SQLCTL01.appliance_domain.pdw.local`です。  
  
たとえば、PDW 地域名 MyPDW、アプライアンスの名前は MyAPS dwloader のサーバーのデータを読み込むための仕様は、次のいずれか。  
  
-   `dwloader –S MYPDW-SQLCTL01.MyAPS.pdw.local`  
  
-   `dwloader –S MYPDW-SQLCTL01`  
  
## <a name="BeforeBegin"></a>はじめに  
  
### <a name="requirements"></a>必要条件  
APS アプライアンスのドメイン アカウント、AD01 ノードへのログインにする必要があります。 たとえば、F12345 * \Administrator です。  
  
ネットワーク アダプターを構成する権限を持つクライアント サーバーで Windows アカウントが必要です。  
  
### <a name="prerequisites"></a>Prerequisites  
これらの手順では、クライアント サーバーのラックおよびアプライアンスの InfiniBand ネットワークに配線されていると仮定します。 ラック マウントと指示をケーブルは、次を参照してください。[取得および構成を読み込むサーバー](acquire-and-configure-loading-server.md)です。  
  
### <a name="general-remarks"></a>全般的な解説  
SQLCTL01 を使用すると、分析プラットフォーム システム DNS は、クライアント サーバー接続管理ノードに作業中の InfiniBand ネットワークを使用しています。 これは; 接続にのみ適用されます。InfiniBand ネットワークがダウンした場合の負荷やバックアップ中に、プロセスを再起動する必要があります。  
  
独自のビジネス要件を満たすためには、クライアント サーバーをアプライアンス以外のワークグループまたは Windows ドメインに参加することもできます。  
  
## <a name="Sec1"></a>手順 1: は、アプライアンスの InfiniBand ネットワークの設定を取得します。  
*アプライアンスの InfiniBand ネットワークの設定を取得するには*  
  
1.  Appliance_domain\Administrator アカウントを使用してアプライアンス AD01 ノードにログインします。  
  
2.  アプライアンス AD01 ノードで、コントロール パネルを開き、ネットワークおよびインターネット、ネットワークと共有センター * を選択およびアダプター設定の変更を選択します。  
  
3.  ネットワーク接続 ウィンドウで、チーム IB1 上を右クリックし、プロパティ を選択します。  
  
    ![管理ノード上の InfiniBand 接続](media/network-teamib.png "管理ノード上の InfiniBand 接続")  
  
4.  値を書き留めて、インターネット プロトコル バージョン 4 (Tcp/ipv4) のプロパティ ウィンドウから、 **IP アドレス**と**サブネット マスク**です。  IP アドレス、  ***appliance_domain*-AD01**ノードは、分析プラットフォーム システム DNS サーバーの IP アドレス。  
  
5.  TeamIB1 アダプターの 1 ~ 5 の上記の手順を繰り返します ***appliance_domain*-AD02**サーバー。  
  
    ![PDW 管理ノード InfiniBand 1 プロパティ](media/network-ip1-properties.png "PDW 管理ノード InfiniBand 1 のプロパティ")  
  
6.  ウィンドウを閉じるには、[キャンセル] をクリックします。  
  
7.  TeamIB1 ネットワーク上の未使用の IP アドレスを検索し、それを書き留めます。  
  
    未使用の IP アドレスを検索するには、コマンド ウィンドウを開き、アプライアンスのアドレスの範囲内の IP アドレスに ping を実行しようとしてください。 この例では、TeamIB1 ネットワークの IP アドレスは、172.16.14.30 がします。 使用されていない 172.16.14 で始まる IP アドレスを検索します。 たとえば、コマンドラインから"172.16.14.254 ping"を入力します。 Ping 要求が成功しなかった場合は、IP アドレスを使用します。  
  
8.  TeamIB2 のプロパティには、同じ処理を行います。 * ネットワーク接続 ウィンドウでは、チーム IB2 を右クリックし、プロパティを選択します。  
  
9. インターネット プロトコル バージョン 4 (Tcp/ipv4) のプロパティ ウィンドウからは、TeamIB2 の IP アドレスとサブネット マスクの値を書き留めます。  
  
10. Appliance_domain AD02 サーバー上の TeamIB2 アダプターには、8 ~ 9 の上記の手順を繰り返します。  
  
    ![TeamIB2 の](media/network-ip2-properties.png "TeamIB2 のプロパティ")  
  
11. 未使用の IP アドレスを確認、 **TeamIB2**ネットワーク、およびを書き留めます。  
  
    未使用の IP アドレスを検索するには、コマンド ウィンドウを開き、アプライアンスのアドレスの範囲内の IP アドレスに ping を実行しようとしてください。 この例では、TeamIB2 のネットワークの IP アドレスは、172.16.18.30 がします。 使用されていない 172.16.18 で始まる IP アドレスを検索します。 たとえば、コマンドラインから"172.16.18.254 ping"を入力します。 Ping 要求が成功しなかった場合は、IP アドレスを使用します。  
  
## <a name="Sec2"></a>手順 2: クライアント サーバー上の InfiniBand ネットワーク アダプターの設定を構成します。  

### <a name="notes"></a>注  
  
-   次の手順では、AP DNS サーバーに、サーバーを登録する方法を示します。  
  
-   ネットワークの要件を満たす、アプライアンス以外のワークグループまたは Windows ドメインにクライアント サーバーを結合することもできます。  
  
-   各サーバーで次の 2 つのネットワーク アダプターの構成方法を指示手順です。  ネットワーク アダプターが 1 つだけの場合は、ネットワーク アダプターで構成し、代替 DNS サーバーとして、2 番目の DNS IP アドレスを追加するようにネットワークのいずれかを選択します。  
  
### <a name="to-configure-the-infiniband-network-adapter-settings-on-your-client-server"></a>クライアント サーバー上の InfiniBand ネットワーク アダプターの設定を構成するには  
  
1.  読み込み、バックアップ、またはアプライアンスの InfiniBand ネットワーク上の他のクライアント サーバー、Windows 管理者としてログインします。  
  
2.  開くコントロール ウィンドウ *、ネットワークと共有センターを選択し、アダプターの設定を変更します。  
  
### <a name="to-configure-the-first-network-adapter"></a>最初のネットワーク アダプターを構成するには  
  
1.  ネットワーク接続 ウィンドウで、Mellanox アダプターの識別されていないネットワーク スロットのいずれかを右クリックし、プロパティを選択します。  
  
    ![InfiniBand ネットワークを選択して](media/network-connections.png "InfiniBand ネットワークの選択")  
  
2.  [プロパティ] ウィンドウ  
  
    1.  [全般] タブには、free TeamIB1 の ping テストとして検証済み IP アドレスを IP アドレスを設定します。 このトピックで使用される値の例は 172.16.14.254 を入力します。  
  
    2.  サブネット マスクを TeamIB1 にメモしたサブネット マスクを設定します。  
  
    3.  優先 DNS サーバー、IP アドレスに設定してから書き写した appliance_domain * TeamIB1 の-AD01 ノード。  
  
    4.  代替 DNS サーバー、IP アドレスに設定してから書き写した appliance_domain * TeamIB1 の-AD02 ノード。  
  
        ![InfiniBand 1 のネットワーク アダプターのプロパティ](media/network-ib1-properties.png "SQL_Server_PDW_Network_IB1_properties")  
  
    5.  変更を適用するには、[ok] をクリックします。  
  
### <a name="to-configure-the-second-network-adapter"></a>2 番目のネットワーク アダプターを構成するには  
  
1.  ネットワーク アダプターが 1 つしかない場合は、このセクションをスキップします。  
  
2.  ネットワーク接続 ウィンドウで、Mellanox アダプターの 2 番目のスロットの識別されていないネットワークを右クリックし、プロパティ を選択します。  
  
    ![InfiniBand ネットワークを選択して](media/network-connections.png "InfiniBand ネットワークの選択")  
  
3.  [プロパティ] ウィンドウ  
  
    1.  [全般] タブには、free TeamIB2 の ping テストとして検証済み IP アドレスを IP アドレスを設定します。 このトピックで使用される値の例は 172.16.18.254 を入力します。  
  
    2.  TeamIB2 のメモしたサブネット マスクにサブネット マスクを設定します。  
  
    3.  優先 DNS サーバー、IP アドレスに設定してから書き写した appliance_domain * TeamIB2 の-AD01 ノード。  
  
    4.  代替 DNS サーバー、IP アドレスに設定してから書き写した appliance_domain * TeamIB2 の-AD02 ノード。  
  
        > [!NOTE]  
        > ネットワーク アダプター、優先し、それぞれを使用して、アプライアンス AD01 TeamIB1 とアプライアンス AD02 TeamIB1 優先および代替 DNS サーバーとして、代替の DNS サーバーを構成するか、アプライアンス AD01 TeamIB2 を使用して 1 つをしかない場合、アプライアンス AD02 TeamIB2 を優先および代替 DNS サーバーによって、AD の仮想マシンはフェールオーバーされました。  
  
        ![InfiniBand 1 のネットワーク アダプターのプロパティ](media/network-ib1-properties.png "InfiniBand 1 のネットワーク アダプターのプロパティ")  
  
    5.  変更を適用するには、[ok] をクリックします。  
  
### <a name="to-configure-the-dns-suffix"></a>DNS サフィックスを構成するには  
  
1.  ネットワーク接続 ウィンドウで、Mellanox アダプターのネットワークのスロットのいずれかを右クリックし、プロパティを選択します。  
  
2.  [詳細設定] をクリックしてください. ボタンをクリックします。  
  
3.  [TCP/IP 詳細設定] ウィンドウで場合は、追加これらの DNS サフィックスを順に) オプションがないグレー、チェック ボックスと呼ばれるこれら DNS サフィックスを追加 (順序で): アプライアンス ドメイン サフィックスを選択して、[追加] をクリックしています. アプライアンスのドメイン サフィックスになります`appliance_domain.local`  
  
4.  場合は、以下の DNS サフィックス (順序で): オプションがグレーで \software\policies\microsoft\windows NT\DNSClient のレジストリ キーを変更することでこのサーバーに APS ドメインを追加することができます。  
  
    ![TCP/IP 設定](media/network-tcpip.png "TCP/IP 設定")  
  
5.  アドレスを迅速に解決するには、アプライアンス サフィックスの一覧の先頭に移動をお勧めします。  
  
6.  [OK] をクリックします。  
  
7.  使用して、アプライアンスの Infiniband ネットワークに接続できるようになりました、 `PDW_region-SQLCTL01.appliance_domain.local`、または単に`appliance_domain-SQLCTL01`です。 完全名と DNS サフィックスを持つ接続する場合も高速接続を確立する可能性があります。  
  
    MyPDW PDW 地域に MyAPS をという名前のアプライアンスは、という名前の例:  
  
    -   MyPDW SQLCTL01.MyAPS.local  
  
    -   MyPDW SQLCTL01  
  
## <a name="see-also"></a>参照  
[取得し、読み込みサーバーを構成します。](acquire-and-configure-loading-server.md)  
  
