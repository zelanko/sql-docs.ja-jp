---
title: Azure のレプリカ追加ウィザードの使用 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.addreplicawizard.azurereplica.f1
ms.assetid: b89cc41b-07b4-49f3-82cc-bc42b2e793ae
caps.latest.revision: 8
author: rothja
ms.author: jroth
manager: jhubbard
ms.openlocfilehash: c2912564cb2866090f428cd96a2adc9d83faf9cf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36076654"
---
# <a name="use-the-add-azure-replica-wizard-sql-server"></a>Azure のレプリカ追加ウィザードの使用 (SQL Server)
  Azure のレプリカ追加ウィザードは、ハイブリッド IT 環境で新しい Windows Azure VM を作成し、新規または既存の AlwaysOn 可用性グループのセカンダリ レプリカとして構成する場合に使用します。  
  
-   **作業を開始する準備:**  
  
     [前提条件](#Prerequisites)  
  
     [Security](#Security)  
  
-   **レプリカを追加する方法:**  [Azure のレプリカ追加ウィザード (SQL Server Management Studio)](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
 可用性グループに可用性レプリカを追加しない場合、「サーバー インスタンス」および「可用性グループとレプリカ」のセクションを参照してください。[前提条件、制限事項、および AlwaysOn 可用性グループ&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)です。  
  
###  <a name="Prerequisites"></a> 前提条件  
  
-   現在のプライマリ レプリカをホストするサーバー インスタンスに接続されている必要があります。  
  
-   内部設置型サブネットにサイト間 VPN と Windows Azure が構成されたハイブリッド IT 環境が必要です。 詳細については、「 [管理ポータルでのサイト間 VPN の構成](https://azure.microsoft.com/documentation/articles/vpn-gateway-site-to-site-create)」を参照してください。  
  
-   可用性グループに、内部設置型可用性レプリカが含まれている必要があります。  
  
-   可用性グループ リスナーに対するクライアントで、可用性グループが Windows Azure レプリカにフェールオーバーした場合にリスナーとの接続を維持するには、インターネット接続が必要です。  
  
-   **初期データの完全同期を使用するための前提条件** ウィザードでのバックアップの作成およびバックアップへのアクセスには、ネットワーク共有を指定する必要があります。 プライマリ レプリカでは、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] の起動に使用するアカウントにネットワーク共有での読み取り/書き込みファイルシステム権限が必要です。 セカンダリ レプリカでは、アカウントは、ネットワーク共有に対する読み取り権限を持つ必要があります。  
  
     ウィザードを使用して初期データの完全同期を実行できない場合は、セカンダリ データベースを手動で準備する必要があります。 これは、ウィザードの実行前でも実行後でもかまいません。 詳細については、「 [可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)で Always On 可用性グループを作成および構成する方法について説明します。  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 「 [Security](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md#Security)」を参照してください。  
  
##  <a name="SSMSProcedure"></a> Azure のレプリカ追加ウィザードの使用 (SQL Server Management Studio)  
 Azure のレプリカ追加ウィザードは、 [[レプリカの指定] ページ](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md)から起動できます。 このページを開くには、次の 2 つの方法があります。  
  
-   [可用性グループ ウィザードの使用 &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [可用性グループへのレプリカ追加ウィザードの使用 &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
 Azure のレプリカ追加ウィザードを起動したら、次の手順を行います。  
  
1.  まず、Windows Azure サブスクリプションの管理証明書をダウンロードします。 **[ダウンロード]** をクリックして、サインイン ページを開きます。  
  
2.  サインイン ページで、Windows Azure サブスクリプションにサインインします。 サインインすると、ローカル コンピューターに管理証明書がインストールされます。 ウィザードを再度使用する場合は、この管理証明書が自動的に読み込まれます。 複数の管理証明書をダウンロードした場合は、 **[...]** ボタンをクリックして、使用する管理証明書を選択します。  
  
3.  次に、 **[接続]** をクリックしてサブスクリプションに接続します。 接続すると、 **[仮想ネットワーク]** や **[仮想ネットワーク サブネット]** などの Windows Azure のパラメーターがドロップダウン リストに示されています。  
  
4.  新しいセカンダリ レプリカをホストする Windows Azure 仮想マシンの設定を指定します。  
  
     image  
     Windows Azure 仮想マシンに使用する SQL Server イメージの名前  
  
     [VM サイズ]  
     Windows Azure 仮想マシンのサイズ  
  
     [VM 名]  
     Windows Azure 仮想マシンの DNS 名  
  
     [VM ユーザー名]  
     Windows Azure 仮想マシンの既定の管理者のユーザー名  
  
     [VM 管理者パスワード] (および [パスワードの確認入力])  
     Windows Azure 仮想マシンの既定の管理者のパスワード  
  
     [仮想ネットワーク]  
     Windows Azure を配置する仮想ネットワーク  
  
     [仮想ネットワーク サブネット]  
     Windows Azure を配置する仮想ネットワーク サブネット  
  
     [ドメイン]  
     Windows Azure 仮想マシンが参加する Active Directory (AD) ドメイン  
  
     [ドメイン ユーザー名]  
     Windows Azure 仮想マシンをドメインに参加させるために使用される AD ユーザー名  
  
     パスワード  
     Windows Azure 仮想マシンをドメインに参加させるために使用されるパスワード  
  
5.  **[OK]** をクリックして設定をコミットし、Azure のレプリカ追加ウィザードを終了します。  
  
6.  新しいレプリカの場合と同じように、 [[レプリカの指定] ページ](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md) で残りの構成手順を行います。  
  
     可用性グループ ウィザードまたは可用性グループへのレプリカ追加ウィザードを完了すると、構成プロセスにより、Windows Azure での操作 (新しい仮想マシンの作成、AD ドメインへの参加、Windows クラスターへの追加、AlwaysOn 高可用性の有効化、可用性グループへの新しいレプリカの追加) がすべて行われます。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [可用性グループへのセカンダリ レプリカの追加 &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの概要&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [前提条件、制限事項、および AlwaysOn 可用性グループに関する推奨事項&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [可用性グループへのセカンダリ レプリカの追加 &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
  