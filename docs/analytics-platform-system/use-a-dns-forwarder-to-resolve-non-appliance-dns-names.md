---
title: Analytics Platform System に、DNS フォワーダーを使用して |Microsoft ドキュメント"
description: Analytics Platform System のアプライアンス以外の DNS 名を解決するのには、DNS フォワーダーを使用します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 2f707d4c681c695105daf23d5fc640279bb83658
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31544944"
---
# <a name="use-a-dns-forwarder-to-resolve-non-appliance-dns-names-in-analytics-platform-system"></a>Analytics Platform System のアプライアンス以外の DNS 名を解決するのには、DNS フォワーダーを使用します。
Active Directory ドメイン サービスのノードで、DNS フォワーダーを構成することができます (***appliance_domain *-AD01**と ***appliance_domain *-AD02**) の使用できるように、Analytics Platform System アプライアンススクリプトおよび外部のサーバーにアクセスするソフトウェア アプリケーションです。  
  
## <a name="ResolveDNS"></a>DNS フォワーダーを使用します。  
Analytics Platform System アプライアンスは、アプライアンスに含まれていないサーバーの DNS 名の解決を防ぐために構成されます。 Windows ソフトウェア Update Services (WSUS) など、いくつかのプロセスは、アプライアンスの外部のサーバーにアクセスする必要があります。 この使用シナリオ分析プラットフォーム システム DNS をサポートするためには、アプライアンスの外部名を解決するのには外部 DNS サーバーを使用するには、Analytics Platform System ホストとバーチャル マシン (Vm) を許可する外部名転送をサポートするために構成できます。 DNS サフィックスのカスタム構成はサポートされていません、つまり、非アプライアンス サーバー名を解決するのには完全修飾ドメイン名を使用する必要があります。  
  
**DNS の GUI を備えた、DNS フォワーダーを作成するには**  
  
1.  ログオン、***appliance_domain *-AD01**ノード。  
  
2.  DNS マネージャーを開き (**dnsmgmt.msc**)。  
  
3.  サーバーの名前を右クリックし、をクリックして**プロパティ**です。  
  
4.  **詳細** タブで、選択を解除、**再帰 (もフォワーダーを無効になります) を無効にする**オプションをクリックして**適用**)。  
  
5.  クリックして、**フォワーダー**  タブをクリックして**編集**です。  
  
6.  名前解決を提供する外部の DNS サーバーの IP アドレスを入力します。 Vm とアプライアンス内のサーバー (ホスト) は、完全修飾ドメイン名を使用して外部のサーバーに接続されます。  
  
7.  手順 1 ~ 6 を繰り返します、***appliance_domain *-AD02**ノード  
  
**Windows PowerShell を使用して、DNS フォワーダーを作成するには**  
  
1.  ログオン、***appliance_domain *-AD01**ノード。  
  
2.  次の Windows PowerShell スクリプトを実行して、***appliance_domain *-AD01**ノード。 Windows PowerShell スクリプトを実行する前に、IP アドレスを非アプライアンスの DNS サーバーの IP アドレスに置き換えます。  
  
    ```  
    $DNS=Get-WmiObject -class "MicrosoftDNS_Server"  -Namespace "root\microsoftdns"  
    $DNS.Forwarders = ("xxx.xxx.xxx.xxx", "xxx.xxx.xxx.xxx")  
    $DNS.put()  
    ```  
  
3.  同じコマンドを実行、***appliance_domain *-AD02**ノード。  
  
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
  
