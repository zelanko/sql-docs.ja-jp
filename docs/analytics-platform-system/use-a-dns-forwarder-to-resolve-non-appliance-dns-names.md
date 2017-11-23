---
title: "(AP) のアプライアンス以外の DNS 名を解決するのには、DNS フォワーダーを使用します。"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 123d8a83-b7fd-4dc9-90d4-fa01af2d629d
caps.latest.revision: "21"
ms.openlocfilehash: 6e91828bcc64a47d942959a2522af0e53041e027
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="use-a-dns-forwarder-to-resolve-non-appliance-dns-names"></a>非アプライアンスの DNS 名を解決するのには、DNS フォワーダーを使用します。
Active Directory ドメイン サービスのノードで、DNS フォワーダーを構成することができます (***appliance_domain*-AD01**と ***appliance_domain*-AD02**)スクリプトとのソフトウェア アプリケーションを外部のサーバーにアクセスできるようにする、Analytics Platform System アプライアンスです。  
  
## <a name="ResolveDNS"></a>DNS フォワーダーを使用します。  
Analytics Platform System アプライアンスは、アプライアンスに含まれていないサーバーの DNS 名の解決を防ぐために構成されます。 Windows ソフトウェア Update Services (WSUS) など、いくつかのプロセスは、アプライアンスの外部のサーバーにアクセスする必要があります。 この使用シナリオ分析プラットフォーム システム DNS をサポートするためには、アプライアンスの外部名を解決するのには外部 DNS サーバーを使用するには、Analytics Platform System ホストとバーチャル マシン (Vm) を許可する外部名転送をサポートするために構成できます。 DNS サフィックスのカスタム構成はサポートされていません、つまり、非アプライアンス サーバー名を解決するのには完全修飾ドメイン名を使用する必要があります。  
  
**DNS の GUI を備えた、DNS フォワーダーを作成するには**  
  
1.  ログオン、  ***appliance_domain*-AD01**ノード。  
  
2.  DNS マネージャーを開き (**dnsmgmt.msc**)。  
  
3.  サーバーの名前を右クリックし、をクリックして**プロパティ**です。  
  
4.  **詳細** タブで、選択を解除、**再帰 (もフォワーダーを無効になります) を無効にする**オプションをクリックして**適用**)。  
  
5.  クリックして、**フォワーダー**  タブをクリックして**編集**です。  
  
6.  名前解決を提供する外部の DNS サーバーの IP アドレスを入力します。 Vm とアプライアンス内のサーバー (ホスト) は、完全修飾ドメイン名を使用して外部のサーバーに接続されます。  
  
7.  手順 1 ~ 6 を繰り返します、  ***appliance_domain*-AD02**ノード  
  
**Windows PowerShell を使用して、DNS フォワーダーを作成するには**  
  
1.  ログオン、  ***appliance_domain*-AD01**ノード。  
  
2.  次の Windows PowerShell スクリプトを実行して、  ***appliance_domain*-AD01**ノード。 Windows PowerShell スクリプトを実行する前に、IP アドレスを非アプライアンスの DNS サーバーの IP アドレスに置き換えます。  
  
    ```  
    $DNS=Get-WmiObject -class "MicrosoftDNS_Server"  -Namespace "root\microsoftdns"  
    $DNS.Forwarders = ("xxx.xxx.xxx.xxx", "xxx.xxx.xxx.xxx")  
    $DNS.put()  
    ```  
  
3.  同じコマンドを実行、  ***appliance_domain*-AD02**ノード。  
  
## <a name="configuring-dns-resolution-for-wsus"></a>WSUS の DNS 解決を構成します。  
SQL Server PDW 2012 では、統合サービスと機能を修正プログラムを提供します。 SQL Server PDW では、Microsoft Update と他の Microsoft テクノロジのサービスを使用します。 更新プログラムを有効にするには、アプライアンスは企業 WSUS リポジトリまたは Microsoft パブリック WSUS リポジトリをするか、接続できる必要があります。  
  
Microsoft パブリック WSUS リポジトリで更新プログラムを検索するアプライアンスを構成することを選択している場合は、次の手順は、アプライアンス上適切な構成の詳細を設定します。  
  
> [!NOTE]  
> 顧客は、ネットワーク管理者で名前を解決できる会社の DNS サーバーの IP アドレスを指定する必要があります**Microsoft.com**です。  
  
1.  VMM の VM にログインして、リモート デスクトップを使用して (<fabric domain>VMM) ファブリック ドメイン管理者アカウントを使用します。  
  
2.  コントロール パネルを開き、**ネットワークとインターネット**、クリックして**ネットワークと共有センター**です。  
  
3.  接続の一覧で**VMSEthernet**、順にクリック**プロパティ**です。  
  
4.  選択**インターネット プロトコル バージョン 4 (Tcp/ipv4)**、クリックして**プロパティ**です。  
  
5.  **代替 DNS サーバー**ボックスで、お客様のネットワーク管理者によって提供された IP アドレスを追加します。  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
