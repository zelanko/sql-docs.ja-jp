---
title: Analytics Platform System で DNS フォワーダーの使用 |Microsoft Docs"
description: Analytics Platform System で非アプライアンス DNS 名を解決するのにには、DNS フォワーダーを使用します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 841d2da521bada840c1298d3fb9cea28c2835b4a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959826"
---
# <a name="use-a-dns-forwarder-to-resolve-non-appliance-dns-names-in-analytics-platform-system"></a>DNS フォワーダーを使用して、Analytics Platform System で非アプライアンス DNS 名を解決するのには
Active Directory ドメイン サービス ノードで DNS フォワーダーを構成することができます ( **_アプライアンス\_ドメイン_-AD01** と **_アプライアンス\_ドメイン_-AD02** ) のスクリプトとソフトウェア アプリケーションの外部サーバーへのアクセスを許可する、Analytics Platform System appliance。  
  
## <a name="ResolveDNS"></a>DNS フォワーダーを使用します。  
Analytics Platform System appliance では、アプライアンスではありません。 サーバーの DNS 名の解決されないように構成されます。 Windows Software Update Services (WSUS) など、一部のプロセスは、アプライアンスの外部にあるサーバーにアクセスする必要があります。 この使用シナリオの Analytics プラットフォームの DNS システムをサポートするためには、外部 DNS サーバーを使用して、アプライアンス外の名前を解決するには、Analytics Platform System のホストとバーチャル マシン (Vm) を許可する外部名転送をサポートするために構成できます。 DNS サフィックスのカスタム構成サポートされていません、つまり、非アプライアンス サーバー名を解決するのには、完全修飾ドメイン名を使用する必要があります。  
  
**DNS の GUI で DNS フォワーダーを作成するには**  
  
1.  ログオン、 **_アプライアンス\_ドメイン_-AD01** ノード。  
  
2.  DNS マネージャーを開き (**dnsmgmt.msc**)。  
  
3.  サーバーの名前を右クリックし、をクリックし、**プロパティ**します。  
  
4.  **詳細設定**  タブで、選択を解除、**再帰 (もフォワーダーを無効になります) を無効にする**オプションをクリックして**適用**)。  
  
5.  をクリックして、**フォワーダー**  タブをクリックして**編集**します。  
  
6.  名前解決を提供する外部の DNS サーバーの IP アドレスを入力します。 Vm と、アプライアンス内のサーバー (ホスト) は、完全修飾ドメイン名を使用して外部のサーバーに接続されます。  
  
7.  手順 1. ~ 6. を繰り返します、 **_アプライアンス\_ドメイン_-AD02** ノード  
  
**Windows PowerShell を使用して、DNS フォワーダーを作成するには**  
  
1.  ログオン、 **_アプライアンス\_ドメイン_-AD01** ノード。  
  
2.  次の Windows PowerShell スクリプトの実行、 **_アプライアンス\_ドメイン_-AD01** ノード。 Windows PowerShell スクリプトを実行する前に、非アプライアンス DNS サーバーの IP アドレスと IP アドレスを置き換えます。  
  
    ```  
    $DNS=Get-WmiObject -class "MicrosoftDNS_Server"  -Namespace "root\microsoftdns"  
    $DNS.Forwarders = ("xxx.xxx.xxx.xxx", "xxx.xxx.xxx.xxx")  
    $DNS.put()  
    ```  
  
3.  同じコマンドを実行、 **_アプライアンス\_ドメイン_-AD02** ノード。  
  
## <a name="configuring-dns-resolution-for-wsus"></a>WSUS の DNS 解決の構成  
SQL Server PDW 2012 では、統合のサービスと機能の修正を提供します。 SQL Server PDW では、Microsoft Update と他の Microsoft のテクノロジのサービスを使用します。 アプライアンスは、更新プログラムを有効にするには、か、企業 WSUS リポジトリまたは Microsoft のパブリック WSUS リポジトリに接続できる必要があります。  
  
Microsoft パブリック WSUS リポジトリで更新プログラムを検索するアプライアンスを構成し、お客様の場合は、次の手順は、アプライアンスの適切な構成の詳細を設定します。  
  
> [!NOTE]  
> 顧客のネットワーク管理者に名前を解決できる会社の DNS サーバーの IP アドレスを指定する必要があります**Microsoft.com**します。  
  
1.  リモート デスクトップ、VMM の VM にログオンを使用して (<fabric domain>VMM) ファブリックのドメイン管理者アカウントを使用します。  
  
2.  コントロール パネルを開き、[**ネットワークとインターネット**、] をクリックし、**ネットワークと共有センター**します。  
  
3.  [接続の一覧で**VMSEthernet**、] をクリックし、**プロパティ**します。  
  
4.  選択**インターネット プロトコル バージョン 4 (Tcp/ipv4)** 、 をクリックし、**プロパティ**します。  
  
5.  **代替 DNS サーバー**ボックスで、顧客のネットワーク管理者によって提供される IP アドレスを追加します。  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
