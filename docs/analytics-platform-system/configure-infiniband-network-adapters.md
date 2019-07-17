---
title: Analytics Platform System を構成するには、InfiniBand、|Microsoft Docs
description: コントロールのノードで並列データ ウェアハウス (PDW) に接続するクライアントの非アプライアンス サーバーで、InfiniBand ネットワーク アダプターを構成する方法について説明します。 読み込むように基本的な接続性と高可用性のために次の手順を使用して、バックアップ、およびその他のプロセスが自動的にアクティブな InfiniBand ネットワークに接続します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 4739a79989321c215819bab90da1d1831764f820
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961245"
---
# <a name="configure-infiniband-network-adapters-for-analytics-platform-system"></a>Analytics Platform System の InfiniBand ネットワーク アダプターを構成します。
コントロールのノードで並列データ ウェアハウス (PDW) に接続するクライアントの非アプライアンス サーバーで、InfiniBand ネットワーク アダプターを構成する方法について説明します。 読み込むように基本的な接続性と高可用性のために次の手順を使用して、バックアップ、およびその他のプロセスが自動的にアクティブな InfiniBand ネットワークに接続します。  
  
## <a name="Basics"></a>説明  
この手順では、検索し、設定正しい InfiniBand IP アドレスとサブネット マスク、InfiniBand 接続されているサーバーにする方法を示します。 また、接続がアクティブの InfiniBand ネットワークに解決できるように、APS アプライアンス DNS を使用するようにサーバーを設定する方法を説明します。  
  
高可用性、AP が 2 つの InfiniBand ネットワーク、1 つのアクティブおよびパッシブの 1 つ。 各 InfiniBand ネットワークには、コントロールのノードに異なる IP アドレスがあります。 Active の InfiniBand ネットワークがダウンした場合、パッシブの InfiniBand ネットワークはアクティブなネットワークになります。 このような場合、スクリプトまたはプロセスに自動的に接続 active の InfiniBand ネットワーク スクリプトのパラメーターを変更することがなく。  
  
具体的には、このことを記事します。  
  
1.  サーバーのアクセス ポイントの DNS の InfiniBand IP アドレスを検索 (appliance_domain AD01 と appliance_domain *-AD02)。 これを行うには、AD01 と AD02 サーバーにログインし、各 InfiniBand ネットワークの IP アドレスを取得します。 AD ノード上の InfiniBand IP アドレスは、DNS の IP アドレスです。  
  
2.  APS の InfiniBand ネットワークで使用可能な IP アドレスを使用するには、各ネットワーク アダプターを構成します。  
  
    1.  2 つの InfiniBand ネットワーク アダプターがあれば、TeamIB2 と呼ばれる 2 つ目の InfiniBand ネットワーク TeamIB1、およびその他のアダプターの使用可能な IP アドレスと呼び出される最初の InfiniBand ネットワークで使用可能な IP アドレスを持つ 1 つのアダプターを構成します。 優先 DNS サーバーと appliance_domain AD02 TeamIB1 appliance_domain AD01 TeamIB1 を使用して IP アドレスとして TeamIB1 ネットワーク アダプターの代替 DNS サーバーの IP アドレス。 優先 DNS サーバーと appliance_domain AD02 TeamIB2 appliance_domain AD01 TeamIB2 を使用して IP アドレスとして TeamIB2 のネットワーク アダプターの代替 DNS サーバーの IP アドレス。  
  
    2.  InfiniBand ネットワーク アダプターの 1 つだけの場合は、InfiniBand ネットワークのいずれかから使用可能な IP アドレスとアダプターを構成します。 Appliance_domain AD01 TeamIB1 と appliance_domain AD02 TeamIB1 のいずれかを使用するか、appliance_domain AD01 TeamIB2 と appliance_domain AD02 TeamIB2 を使用して、同じ方は、このアダプターで、優先および代替 DNS サーバーを構成する、優先として構成されているアダプターと代替の DNS サーバーとして、それぞれネットワークです。  
  
3.  Active の InfiniBand ネットワークに接続を解決するのにはアクセス ポイントの DNS サーバーを使用する、InfiniBand ネットワーク アダプターを構成します。  
  
    1.  これを構成するには TCP/IP 詳細設定を使用して、クライアント サーバーの DNS サフィックスの一覧の先頭にアプライアンスのドメインの DNS サフィックスを追加します。 これは、のみ; のネットワーク アダプターのいずれかで構成する必要があります。設定は、両方のアダプターに適用されます。  
  
InfiniBand ネットワーク アダプターを構成すると、クライアント プロセスに接続できる InfiniBand ネットワーク上の管理ノードを使用して`PDW_region-SQLCTL01`サーバーのアドレス。 サーバーは、Analytics Platform System の DNS サフィックスを追加するかは完全なアドレスを入力することができます`PDW_region-SQLCTL01.appliance_domain.pdw.local`します。  
  
たとえば、PDW 地域名が MyPDW アプライアンス名が MyAPS、dwloader サーバー仕様は、データの読み込みです、次のいずれか。  
  
-   `dwloader -S MYPDW-SQLCTL01.MyAPS.pdw.local`  
  
-   `dwloader -S MYPDW-SQLCTL01`  
  
## <a name="BeforeBegin"></a>はじめに  
  
### <a name="requirements"></a>必要条件  
APS アプライアンスのドメイン アカウント AD01 ノードにログインする必要があります。 たとえば、F12345 * \Administrator します。  
  
ネットワーク アダプターを構成する権限を持つクライアント サーバー上の Windows アカウントが必要です。  
  
### <a name="prerequisites"></a>必須コンポーネント  
これらの手順では、クライアント サーバーが既にラックし、アプライアンスの InfiniBand ネットワークに接続されていると仮定します。 ラック構成と手順を配線を参照してください。[の取得と構成を読み込むサーバー](acquire-and-configure-loading-server.md)します。  
  
### <a name="general-remarks"></a>全般的な解説  
SQLCTL01 を使用すると、Analytics Platform System の DNS は、コントロール ノードに、クライアント サーバーはアクティブの InfiniBand ネットワークを使用して接続します。 これは接続のみに適用されます。負荷やバックアップの InfiniBand ネットワークがダウンした場合は、プロセスを再起動する必要があります。  
  
独自のビジネス要件を満たすには、非アプライアンス ワークグループまたは Windows ドメインにもクライアント サーバーを結合できます。  
  
## <a name="Sec1"></a>手順 1:アプライアンスの InfiniBand ネットワークの設定を取得します。  
*アプライアンスの InfiniBand ネットワークの設定を取得するには*  
  
1.  ログイン アプライアンス AD01 ノード appliance_domain\Administrator アカウントを使用します。  
  
2.  アプライアンス AD01 ノードで、コントロール パネルを開き、ネットワークおよびインターネット、[ネットワークと共有センター * を選択およびアダプター設定の変更] を選択します。  
  
3.  ネットワーク接続 ウィンドウで、チーム IB1 を右クリックし、プロパティを選択します。  
  
    ![管理ノード上の InfiniBand 接続](media/network-teamib.png "管理ノード上の InfiniBand 接続")  
  
4.  インターネット プロトコル バージョン 4 (Tcp/ipv4) のプロパティ ウィンドウからの値を書き込み、 **IP アドレス**と**サブネット マスク**します。  IP アドレス、 **_アプライアンス\_ドメイン_-AD01**ノードは、Analytics Platform System の DNS サーバーの IP アドレス。  
  
5.  TeamIB1 アダプターの 1 ~ 5 の上記の手順を繰り返します **_アプライアンス\_ドメイン_-AD02** サーバー。  
  
    ![PDW 管理ノード InfiniBand 1 プロパティ](media/network-ip1-properties.png "PDW 管理ノード InfiniBand 1 のプロパティ")  
  
6.  ウィンドウを閉じるには、[キャンセル] をクリックします。  
  
7.  TeamIB1 ネットワークで未使用の IP アドレスを見つけてメモします。  
  
    未使用の IP アドレスを検索するには、コマンド ウィンドウを開き、アプライアンスのアドレスの範囲内の IP アドレスに対して ping を実行します。 この例では、TeamIB1 ネットワークの IP アドレスは、172.16.14.30 が。 使用されていない 172.16.14 で始まる IP アドレスを検索します。 たとえば、コマンドラインから"ping 172.16.14.254"入力します。 Ping 要求が成功しなかった場合は、IP アドレスを使用します。  
  
8.  TeamIB2 のプロパティには、同じ操作を行います。 \* ネットワーク接続 ウィンドウでは、チーム IB2 を右クリックし、プロパティを選択します。  
  
9. インターネット プロトコル バージョン 4 (Tcp/ipv4) のプロパティ ウィンドウからには、TeamIB2 の IP アドレスとサブネット マスクの値を書き留めます。  
  
10. TeamIB2 アダプター appliance_domain AD02 サーバー上の 8 ~ 9 の上記の手順を繰り返します。  
  
    ![TeamIB2 の](media/network-ip2-properties.png "TeamIB2 のプロパティ")  
  
11. 上の未使用の IP アドレスの検索、 **TeamIB2**ネットワーク、およびメモします。  
  
    未使用の IP アドレスを検索するには、コマンド ウィンドウを開き、アプライアンスのアドレスの範囲内の IP アドレスに対して ping を実行します。 この例では、TeamIB2 のネットワークの IP アドレスは、172.16.18.30 が。 使用されていない 172.16.18 で始まる IP アドレスを検索します。 たとえば、コマンドラインから"ping 172.16.18.254"入力します。 Ping 要求が成功しなかった場合は、IP アドレスを使用します。  
  
## <a name="Sec2"></a>手順 2:クライアント サーバー上の InfiniBand ネットワーク アダプターの設定を構成します。  

### <a name="notes"></a>メモ  
  
-   次の手順では、サーバーのアクセス ポイントの DNS サーバーを登録する方法を示します。  
  
-   ネットワークの要件を満たすために、クライアント サーバーを非アプライアンス ワークグループまたは Windows ドメインにも参加できます。  
  
-   手順については、2 つのネットワーク アダプターを構成する各サーバー上の手順します。  ネットワーク アダプターが 1 つだけの場合、ネットワーク アダプターで構成し、代替の DNS サーバーとして 2 番目の DNS の IP アドレスを追加するネットワークのいずれかを選択します。  
  
### <a name="to-configure-the-infiniband-network-adapter-settings-on-your-client-server"></a>クライアント サーバー上の InfiniBand ネットワーク アダプターの設定を構成するには  
  
1.  ログインには、Windows 管理者として、読み込み、バックアップ、またはアプライアンス上の他のクライアント サーバーの InfiniBand ネットワークします。  
  
2.  コントロール ウィンドウ * を開く、ネットワークと共有センター を選択し、アダプター設定の変更 を選択します。  
  
### <a name="to-configure-the-first-network-adapter"></a>最初のネットワーク アダプターを構成するには  
  
1.  ネットワーク接続 ウィンドウで、Mellanox アダプターの不明なネットワークのスロットのいずれかを右クリックし、プロパティを選択します。  
  
    ![InfiniBand ネットワークを選択して](media/network-connections.png "InfiniBand ネットワークの選択")  
  
2.  [プロパティ] ウィンドウ  
  
    1.  [全般] タブには、TeamIB1 の ping テストで無料として検証した IP アドレスを IP アドレスを設定します。 この記事で使用される値の例は 172.16.14.254 を入力します。  
  
    2.  サブネット マスクを TeamIB1 にメモしたサブネット マスクを設定します。  
  
    3.  前の appliance_domain * からメモした TeamIB1 の IP アドレスを優先 DNS サーバーの設定-AD01 ノード。  
  
    4.  前の appliance_domain * からメモした TeamIB1 の IP アドレスを代替 DNS サーバーの設定-AD02 ノード。  
  
        ![1 つのネットワーク アダプターのプロパティの InfiniBand](media/network-ib1-properties.png "SQL_Server_PDW_Network_IB1_properties")  
  
    5.  変更を適用するには、[ok] をクリックします。  
  
### <a name="to-configure-the-second-network-adapter"></a>2 番目のネットワーク アダプターを構成するには  
  
1.  ネットワーク アダプターが 1 つしかない場合は、このセクションをスキップします。  
  
2.  ネットワーク接続 ウィンドウでは、2 番目のスロットの識別されていないネットワーク Mellanox アダプターを右クリックし、プロパティを選択します。  
  
    ![InfiniBand ネットワークを選択して](media/network-connections.png "InfiniBand ネットワークの選択")  
  
3.  [プロパティ] ウィンドウ  
  
    1.  [全般] タブには、TeamIB2 の ping テストで無料として検証した IP アドレスを IP アドレスを設定します。 この記事で使用される値の例は 172.16.18.254 を入力します。  
  
    2.  TeamIB2 のメモしたサブネット マスクをサブネット マスクを設定します。  
  
    3.  前の appliance_domain * からメモした TeamIB2 の IP アドレスを優先 DNS サーバーの設定-AD01 ノード。  
  
    4.  前の appliance_domain * からメモした TeamIB2 の IP アドレスを代替 DNS サーバーの設定-AD02 ノード。  
  
        > [!NOTE]  
        > ネットワーク アダプター、構成、優先および代替 DNS サーバーが、優先および代替 DNS サーバーとして、アプライアンス AD01 TeamIB1 とアプライアンス AD02 TeamIB1 をそれぞれ使用または AD01 TeamIB2 のアプライアンスを使用して、1 つをしかない場合、アプライアンス AD02 TeamIB2 を優先し、場合に応じて代替 DNS サーバーは、AD の仮想マシンをフェールオーバーしました。  
  
        ![1 つのネットワーク アダプターのプロパティの InfiniBand](media/network-ib1-properties.png "InfiniBand 1 つのネットワーク アダプターのプロパティ")  
  
    5.  変更を適用するには、[ok] をクリックします。  
  
### <a name="to-configure-the-dns-suffix"></a>DNS サフィックスを構成するには  
  
1.  ネットワーク接続 ウィンドウで、Mellanox アダプターのネットワークのスロットのいずれかを右クリックし、プロパティを選択します。  
  
2.  ... ボタンを 詳細設定 をクリックします。  
  
3.  TCP/IP 詳細設定 ウィンドウで場合追加これら DNS サフィックス (順番に) オプションはありません灰色、チェック ボックスと呼ばれる追加順序でこれらの DNS サフィックス: アプライアンスのドメイン サフィックスを選び、追加 をクリックしています.アプライアンスのドメイン サフィックスが `appliance_domain.local`  
  
4.  (順序) でこれらの DNS サフィックスを追加する場合: オプションは灰色、\software\policies\microsoft\windows NT\DNSClient レジストリ キーを変更することで、このサーバーに APS ドメインを追加できます。  
  
    ![TCP/IP 設定](media/network-tcpip.png "TCP/IP 設定")  
  
5.  アドレスを迅速に解決するには、アプライアンスのサフィックスを一覧の先頭に移動をお勧めします。  
  
6.  [OK] をクリックします。  
  
7.  使用してアプライアンスの Infiniband ネットワークに接続できるようになりました、 `PDW_region-SQLCTL01.appliance_domain.local`、または単に`appliance_domain-SQLCTL01`します。 DNS サフィックスと完全な名前で接続する場合は、接続を高速確立可能性があります。  
  
    アプライアンスの例では、MyPDW PDW リージョン MyAPS という名前。  
  
    -   MyPDW SQLCTL01.MyAPS.local  
  
    -   MyPDW SQLCTL01  
  
## <a name="see-also"></a>関連項目  
[取得し、読み込みサーバーの構成](acquire-and-configure-loading-server.md)  
  
