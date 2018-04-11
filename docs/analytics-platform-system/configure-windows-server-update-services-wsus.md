---
title: Windows Server Update Services (WSUS) (Analytics Platform System) を構成します。
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a10b2884-468e-41ef-bd59-8df894381254
caps.latest.revision: 41
ms.openlocfilehash: 31427bc55017cf9c069e8cd4a467dfdb9608ca3f
ms.sourcegitcommit: d6b1695c8cbc70279b7d85ec4dfb66a4271cdb10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2018
---
# <a name="configure-windows-server-update-services-wsus"></a>Windows Server Update Services (WSUS) を構成します。
これらの手順では、Windows Server Update Services (WSUS) の構成ウィザードを使用して、Analytics Platform System の WSUS を構成するための手順について説明します。 アプライアンスにソフトウェア更新プログラムを適用する前に、WSUS を構成する必要があります。 WSUS は、アプライアンスの VMM のバーチャル マシンに既にインストールされています。  
  
WSUS の構成の詳細については、次を参照してください。、 [WSUS ステップ バイ ステップのインストール ガイド](http://go.microsoft.com/fwlink/?LinkId=202417)、WSUS web サイトです。 WSUS を構成した後、次を参照してください。[ダウンロードと Microsoft 更新プログラムの適用&#40;Analytics Platform System&#41; ](download-and-apply-microsoft-updates.md)更新を開始します。  
  
> [!WARNING]  
> この構成プロセス中にエラーが発生した場合は、停止し、サポートにお問い合わせします。 エラーを無視したり、エラーが発生した後、プロセスの続行しないでください。  
  
## <a name="before-you-begin"></a>はじめに  
WSUS を構成する必要があります。  
  
-   Analytics Platform System アプライアンス ドメイン管理者アカウントのログイン情報があります。  
  
-   Analytics Platform System にアクセスする権限を持つログインを持つ、**管理コンソール**とアプライアンスの状態情報を表示します。  
  
-   Microsoft Update から直接更新を同期するのではなく、上流の WSUS サーバーから更新プログラムを同期するために計画している場合は、アップ ストリーム WSUS サーバーの IP アドレスを把握します。 アップ ストリーム WSUS サーバーが匿名接続を許可に設定されており、SSL をサポートしていることを確認してください。  
  
-   アプライアンスが上流サーバーまたは Microsoft Update にアクセスするプロキシ サーバーを使用する場合は、プロキシ サーバーの IP アドレスを把握します。  
  
-   ほとんどの場合、WSUS は、アプライアンスの外部のサーバーにアクセスする必要があります。 外部名を解決するのには外部 DNS サーバーを使用するには、Analytics Platform System ホストとバーチャル マシン (Vm) を許可する外部名転送をサポートするために分析プラットフォーム システム DNS を構成することができます、この使用シナリオをサポートするために、アプライアンスです。 詳細については、次を参照してください。[非アプライアンス DNS 名の解決に DNS フォワーダーを使用して&#40;Analytics Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)です。  
  
## <a name="to-configure-windows-server-update-services-wsus"></a>Windows Server Update Services (WSUS) を構成するには  
  
1.  ログイン、**管理コンソール**です。 **のアプライアンス状態** タブであることを確認、**クラスター**と**ネットワーク**緑の列を表示する (または**NA**) のすべてのノードです。 上のすべてのノードの状態インジケーターを確認してください、**のアプライアンス状態**です。  
  
    -   緑または NA インジケーターを続行する安全です。  
  
    -   重大でない (黄色) 警告エラーを評価します。 場合によっては警告メッセージには 更新プログラムはブロックされません。 C:\ ドライブにないに重大でないディスク ボリューム エラーがある場合、ディスク ボリュームのエラーを解決する前に、次の手順を続行することができます。  
  
    -   ほとんどの赤のインジケーターは、続行する前に解決する必要があります。 ディスクの障害がある場合を使用して、**管理者コンソールのアラート**ページを各サーバーまたは SAN 配列内の 2 つ以上のディスク障害があることを確認します。 各サーバーまたは SAN 配列内の 2 つ以上のディスク障害がある場合、ディスク エラーを修正する前に、次の手順を続行することができます。 ディスクの障害をできるだけ早く修正を Microsoft サポートに問い合わせることを確認します。  
  
2.  VMM バーチャル マシンにアプライアンス ドメイン管理者としてログオンします。  
  
3.  構成ウィザードを起動します。  
  
    #### <a name="to-launch-the-configuration-wizard"></a>構成ウィザードを起動するには  
  
    1.  **サーバー マネージャー ダッシュ ボード**の**ツール** メニューのをクリックして**Windows Server Update Services**です。  
  
    2.  左側のウィンドウで、 **Update Services**ウィンドウをクリックして仮想マシンの管理ノードのサーバーを展開 (***appliance_domain *-VMM**)、をクリックして**オプション**です。  
  
    3.  **オプション** ウィンドウで、をクリックして**WSUS サーバーの構成ウィザード**構成ウィザードを起動します。  
  
        ![サーバー マネージャー ダッシュ ボード メニュー](./media/configure-windows-server-update-services-wsus/WSUS_Wiz0.png "WSUS_Wiz0")  
  
    4.  初めての場合は、WSUS のウィザードを実行する、更新プログラムを格納するディレクトリを構成するように求められます可能性があります。 `C:\wsus` 適切な場所にはただし、別のパスを指定する場合があります。  
  
        ![WSUS パス](./media/configure-windows-server-update-services-wsus/WSUS_Wiz1.png "WSUS_Wiz1")  
  
    5.  確認、**開始する前に**ウィザードを完了する前に完了する項目の一覧です。  
  
        ![開始する前に WSUS](./media/configure-windows-server-update-services-wsus/WSUS_Wiz2.png "WSUS_Wiz2")  
  
    6.  **Microsoft Update 向上プログラムに参加**] ページで、[**はい、Microsoft Update 向上プログラムに参加したいと考えて**、順にクリック**次**です。  
  
        ![WSUS: 向上プログラム](./media/configure-windows-server-update-services-wsus/WSUS_Wiz3.png "WSUS_Wiz3")  
  
    すると、**上流サーバーの選択**ページ。 次のスクリーン ショットは、構成ウィザードの開始ポイントです。  
  
    ![WSUS Upstream Server Sync](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4a.png "WSUS_Wiz4a")  
  
4.  アップ ストリーム サーバーを選択します。  
  
    **上流サーバーの選択**ページ WSUS 構成ウィザードの仮想マシンの管理 ノードで WSUS がソフトウェア更新プログラムを取得するアップ ストリーム サーバーに接続する方法を選択します。 使用して、アップ ストリーム サーバーを同期するために、2 つの選択肢は、 [Microsoft Update](http://go.microsoft.com/fwlink/?LinkId=133349)または別の Windows Server Update Services サーバーで更新を同期します。  
  
    #### <a name="to-update-by-using-microsoft-update"></a>Microsoft Update を使用して更新するには  
  
    1.  Microsoft Update と同期するために選択する場合は何も変更する必要はありません、**上流サーバーの選択**ページ。 **[次へ]**をクリックします。  
  
        ![WSUS Upstream Server Sync](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4a.png "WSUS_Wiz4a")  
  
    #### <a name="to-update-from-another-wsus-server"></a>別の WSUS サーバーから更新するには  
  
    1.  Microsoft Update (アップ ストリーム サーバー) 以外のソースと同期する場合は、サーバーを指定 (IP アドレスを入力します) とポートをこのサーバーはアップ ストリーム サーバーと通信します。  
  
        ![WSUS: 上流サーバー WSUS から同期](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4b.png "WSUS_Wiz4b")  
  
    2.  Secure Sockets Layer (SSL) を使用するのには、選択、**更新情報の同期時に SSL を使用する**チェック ボックスをオンします。 その場合は、サーバーは同期のポート 443 を使用します。  
  
        ![WSUS: WSUS SSL からアップ ストリーム サーバー同期](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4c.png "WSUS_Wiz4c")  
  
    3.  レプリカ サーバーの場合は、選択、**これが上流サーバーのレプリカ**チェック ボックスをオンします。 両方を選択することは**更新プログラムの情報を同期するときに、SSL を使用して**と**これが上流サーバーのレプリカ**です。  
  
        ![WSUS のアップ ストリーム サーバーのレプリカ](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4d.png "WSUS_Wiz4d")  
  
    4.  この時点では、アップ ストリーム サーバーの構成が完了したらです。 をクリックして**[次へ]**、または選択**プロキシ サーバーの指定**左側のナビゲーション ウィンドウでします。  
  
5.  プロキシ サーバーを指定します。  
  
    このサーバーには、Microsoft Update にアクセスするプロキシ サーバーまたは別のアップ ストリーム サーバーが必要とする場合は、ここでは、プロキシ サーバー設定を構成することができます。それ以外の場合、をクリックして**次**です。  
  
    ![WSUS: プロキシ](./media/configure-windows-server-update-services-wsus/WSUS_Wiz5a.png "WSUS_Wiz5a")  
  
    #### <a name="to-configure-proxy-server-settings"></a>プロキシ サーバー設定を構成するには  
  
    1.  **プロキシ サーバーの指定**構成ウィザード のページ、**を同期するときにプロキシ サーバーを使用して**チェック ボックスをオンし、プロキシ サーバーの IP アドレスが名前ではなく) とポート番号 (ポート 80 で入力既定値)、対応するボックス。  
  
    2.  特定のユーザーの資格情報、選択を使用してプロキシ サーバーに接続する場合、**ユーザーの資格情報を使用してプロキシ サーバーに接続する**チェック ボックスをオンし、対応するユーザー名、ドメイン、およびユーザーのパスワードを入力ボックス。 プロキシ サーバーに接続するユーザーに対して基本認証を有効にする場合、**基本認証を許可する (パスワードはクリア テキストで送信)**チェック ボックスをオンします。  
  
        ![WSUS のプロキシ資格情報](./media/configure-windows-server-update-services-wsus/WSUS_Wiz5b.png "WSUS_Wiz5b")  
  
    3.  この時点では、プロキシ サーバーの構成が完了したらです。 をクリックして**次**ページに移動する、[次へ]、同期プロセスを設定する開始することができます。  
  
6.  接続を開始します。  
  
    ![WSUS: プロキシの接続の開始](./media/configure-windows-server-update-services-wsus/WSUS_Wiz6.png "WSUS_Wiz6")  
  
    をクリックして**の接続の開始**です。  
  
    接続が成功した後にをクリックして**次**ページに移動する、[次へ]、言語を選択できます。  
  
7.  言語を選択します。  
  
    選択**これらの言語でのみ更新プログラムをダウンロード**です。  
  
    選択**英語**、順にクリック**次**です。  
  
    ![言語を選択](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChooseLanguages.png "SQL_Server_PDW_WSUSChooseLanguages")  
  
8.  製品を選択します。  
  
    > [!NOTE]  
    > アップ ストリーム サーバーを使用している場合いないことができますに製品の選択します。 このオプションを使用できない場合は、この手順をスキップします。  
  
    選択したすべての更新プログラムの選択を解除します。  
  
    選択**SQL Server 2014**、 **SQL Server 2016**、 **Windows Server 2012 R2**、および**System Center 2012 R2 の Virtual Machine Manager**、およびをクリックして**次**です。  
  
9. 分類を選択します。  
  
    > [!NOTE]  
    > アップ ストリーム サーバーを使用している場合いないことができますに分類の選択します。  このオプションを使用できない場合は、この手順をスキップします。  
  
    以前に選択したすべての更新プログラムの選択を解除します。  
  
    選択**重要な更新プログラム**と**セキュリティ更新プログラム**、および更新プログラムを Analytics Platform System アプライアンスが同期されます をクリックし、**次**です。  
  
    ![分類の選択](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChooseClassifications.png "SQL_Server_PDW_WSUSChooseClassifications")  
  
10. 同期スケジュールを構成します。  
  
    選択**手動で同期**、順にクリック**次**です。  
  
    ![同期スケジュールの設定](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSyncSchedule.png "SQL_Server_PDW_WSUSSyncSchedule")  
  
11. 初期同期を開始します。  
  
    選択**初期同期を開始**をクリックし、**次**です。  
  
12. 完了します。  
  
    **[完了]**をクリックします。  
  
## <a name="bkmk_WSUSGroup"></a>WSUS でアプライアンス サーバーをグループ化します。  
Analytics Platform System の WSUS を構成した後は、次の手順は、アプライアンスのサーバーをグループ化は。 に追加するすべてのアプライアンス サーバー グループには、WSUS が、アプライアンスのすべてのサーバーにソフトウェア更新プログラムを適用することができます。  
  
> [!NOTE]  
> WSUS システムは非同期に実行するよう設計されています。 アクティビティを開始する結果がありません常に、すぐに更新します。 そのため、コンピューターが WSUS ダイアログ ボックスに表示 まで、しばらくを待機する必要があります。 実行している、 `setup.exe /action=ReportMicrosoftUpdateClientStatus /DomainAdminPassword="<password>"` 、トピックの最後に説明されているコマンド[ダウンロードと Microsoft 更新プログラムの適用&#40;Analytics Platform System&#41; ](download-and-apply-microsoft-updates.md)  ダイアログ ボックスを更新できます。  
  
#### <a name="to-group-the-appliance-servers"></a>アプライアンスのサーバーをグループ化するには  
  
1.  WSUS コンソールを開きを右クリックして**すべてのコンピューター**  をクリックし、**コンピューター グループの追加**です。  
  
    ![コンピューター グループを追加します。] (./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSAddComputerGroup.png "SQL_Server_PDW_WSUSAddComputerGroup")  
  
2.  コンピューター グループの名前"APS"を入力し、クリックして**追加**です。  
  
    ![新しいコンピューター グループの名前を入力します。] (./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSpecifyGroupName.png "SQL_Server_PDW_WSUSSpecifyGroupName")  
  
3.  をクリックして**すべてのコンピューター**でステータスをもう一度、変更、**ステータス**をドロップダウン メニュー**任意**、順にクリック**更新**です。 展開する必要があります**すべてのコンピューター**新しいグループを確認するために、左側のツリー コントロールをクリックして追加しました。  
  
    ![いずれかの状態を変更および更新 をクリックします。] (./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeStatusToAny.png "SQL_Server_PDW_WSUSChangeStatusToAny")  
  
4.  アプライアンス、右クリックし、クリックの一部であるすべてのコンピューターの選択**メンバーシップの変更**です。  
  
    ![すべての PDW コンピューターのメンバーシップを変更します。] (./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeMembership.png "SQL_Server_PDW_WSUSChangeMembership")  
  
5.  チェック ボックスをクリックし、をクリックして作成した新しいコンピュータ グループを選択して**OK**です。  
  
    ![一連のコンピューター グループのメンバーシップ](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSetComputerGroupMembership.png "SQL_Server_PDW_WSUSSetComputerGroupMembership")  
  
6.  新しいコンピュータ グループを選択し、変更、**ステータス**に**任意**、順にクリック**更新**です。 すべてのコンピューターをこのグループに割り当てられているようになりましたおよび右側のウィンドウで表示されている必要があります。 引き続き、ノードなどの警告を表示するときに、通常は安全では**このノードがない状態を報告してまだ**します。  
  
    ![いずれかの状態を変更および更新 をクリックします。] (./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeStatusAnyRefresh.png "SQL_Server_PDW_WSUSChangeStatusAnyRefresh")  
  
