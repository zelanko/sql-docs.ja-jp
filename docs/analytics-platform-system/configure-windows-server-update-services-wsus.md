---
title: -WSUS を構成するには、Analytics Platform System |Microsoft Docs
description: これらの手順では、Windows Server Update Services (WSUS) の構成ウィザードを使用して、Analytics Platform System のように WSUS を構成するための手順を説明します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 16dc05500964bb37e3252edf81aff85042b7abdb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961124"
---
# <a name="configure-windows-server-update-services-wsus-in-analytics-platform-system"></a>Analytics Platform System での Windows Server Update Services (WSUS) の構成します。
これらの手順では、Windows Server Update Services (WSUS) の構成ウィザードを使用して、Analytics Platform System のように WSUS を構成するための手順を説明します。 アプライアンスにソフトウェア更新プログラムを適用する前に、WSUS を構成する必要があります。 WSUS は、アプライアンスの VMM 仮想マシンに既にインストールされています。  
  
WSUS を構成する方法の詳細については、次を参照してください。、 [WSUS ステップ バイ ステップ インストール ガイド](https://go.microsoft.com/fwlink/?LinkId=202417)、WSUS web サイト。 WSUS を構成した後、次を参照してください。[ダウンロードと Microsoft 更新プログラムの適用&#40;Analytics Platform System&#41; ](download-and-apply-microsoft-updates.md)更新を開始します。  
  
> [!WARNING]  
> この構成プロセス中にエラーが発生した場合は、停止し、サポートにお問い合わせします。 エラーを無視したり、エラーが発生した後、プロセスの続行しないでください。  
  
## <a name="before-you-begin"></a>はじめに  
WSUS を構成するには、する必要があります。  
  
-   Analytics Platform System appliance ドメイン管理者アカウントのログイン情報があります。  
  
-   Analytics Platform System にアクセスするアクセス許可を持つログインを持つ、 **Admin Console**アプライアンスの状態情報を表示します。  
  
-   Microsoft Update から直接更新を同期ではなく上流の WSUS サーバーから更新プログラムを同期しようとしている場合は、上流の WSUS サーバーの IP アドレスを把握します。 アップ ストリーム WSUS サーバーが匿名接続を許可する設定は、SSL をサポートして確認します。  
  
-   アプライアンスが上流サーバーまたは Microsoft Update へのアクセスにプロキシ サーバーを使用する場合は、プロキシ サーバーの IP アドレスを把握します。  
  
-   ほとんどの場合、WSUS は、アプライアンスの外部にあるサーバーにアクセスする必要があります。 外部名を解決するのには、外部の DNS サーバーを使用するには、Analytics Platform System のホストと仮想マシン (Vm) を許可する外部名転送をサポートするために、分析プラットフォーム システム DNS を構成できますこの使用シナリオをサポートするために、アプライアンスです。 詳細については、次を参照してください。[非アプライアンス DNS 名の解決に DNS フォワーダーを使用して、 &#40;Analytics Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)します。  
  
## <a name="to-configure-windows-server-update-services-wsus"></a>Windows Server Update Services (WSUS) を構成するには  
  
1.  ログイン、 **Admin Console**します。 **のアプライアンス状態** タブで、いることを確認、**クラスター**と**ネットワーク**緑色の列を表示する (または**NA**) のすべてのノード。 上のすべてのノードの状態インジケーターを確認、**のアプライアンス状態**します。  
  
    -   緑または NA インジケーターを続行しても安全になります。  
  
    -   重大でない (黄色) 警告エラーを評価します。 場合によっては警告メッセージには 更新プログラムはブロックされません。 C:\ ドライブではないに重大でないディスク ボリューム エラーがある場合、ディスク ボリュームのエラーを解決する前に、次の手順に進むことができます。  
  
    -   ほとんどの赤のインジケーターは、続行する前に解決する必要があります。 ディスク障害がある場合は、使用、**管理者コンソールのアラート**ページに各サーバーまたは SAN 配列内で複数のディスク障害が発生したことを確認します。 各サーバーまたは SAN 配列内の複数のディスク障害がある場合、ディスク エラーを修正する前に、次の手順に進むことができます。 できるだけ早くディスク障害を解決する Microsoft サポートに連絡してください。  
  
2.  アプライアンスのドメイン管理者として VMM のバーチャル マシンにログオンします。  
  
3.  構成ウィザードを起動します。  
  
    #### <a name="to-launch-the-configuration-wizard"></a>構成ウィザードを起動するには  
  
    1.  **サーバー マネージャー ダッシュ ボード**の**ツール** メニューのをクリックして**Windows Server Update Services**します。  
  
    2.  左側のウィンドウで、 **Update Services**ウィンドウをクリックして、仮想マシンの管理ノード サーバーの展開 ( **_appliance_domain_VMM**)、をクリックして**オプション**します。  
  
    3.  **オプション**ウィンドウで、をクリックして**WSUS サーバーの構成ウィザード**構成ウィザードを起動します。  
  
        ![サーバー マネージャー ダッシュ ボード メニュー](./media/configure-windows-server-update-services-wsus/WSUS_Wiz0.png "WSUS_Wiz0")  
  
    4.  これが初めてである場合は、WSUS ウィザードを実行する、更新プログラムを格納するディレクトリの構成を求められる可能性があります。 `C:\wsus` 適切な場所です。ただし、別のパスを提供できます。  
  
        ![WSUS パス](./media/configure-windows-server-update-services-wsus/WSUS_Wiz1.png "WSUS_Wiz1")  
  
    5.  レビュー、**開始する前に**ウィザードを完了する前に完了する項目の一覧。  
  
        ![開始する前に WSUS](./media/configure-windows-server-update-services-wsus/WSUS_Wiz2.png "WSUS_Wiz2")  
  
    6.  **Microsoft Update 向上プログラムに参加**] ページで、[**はい、Microsoft Update 向上プログラムに参加したい**、順にクリックします**次**します。  
  
        ![WSUS: 向上プログラム](./media/configure-windows-server-update-services-wsus/WSUS_Wiz3.png "WSUS_Wiz3")  
  
    表示する必要があります、**アップ ストリーム サーバーの選択**ページ。 次のスクリーン ショットは、構成ウィザードの開始ポイントです。  
  
    ![WSUS: 上流サーバーの同期](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4a.png "WSUS_Wiz4a")  
  
4.  アップ ストリーム サーバーを選択します。  
  
    **アップ ストリーム サーバーの選択**ページの WSUS 構成ウィザードで、仮想マシンの管理 ノードで WSUS がソフトウェア更新プログラムを取得するアップ ストリーム サーバーに接続する方法を選択します。 アップ ストリーム サーバーを同期する、2 つの選択肢は[Microsoft Update](https://go.microsoft.com/fwlink/?LinkId=133349)または別の Windows Server Update Services サーバーで更新を同期します。  
  
    #### <a name="to-update-by-using-microsoft-update"></a>Microsoft Update を使用して更新するには  
  
    1.  Microsoft Update と同期を選択する場合は何も変更する必要はありません、**アップ ストリーム サーバーの選択**ページ。 **[次へ]** をクリックします。  
  
        ![WSUS: 上流サーバーの同期](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4a.png "WSUS_Wiz4a")  
  
    #### <a name="to-update-from-another-wsus-server"></a>別の WSUS サーバーから更新するには  
  
    1.  Microsoft Update (アップ ストリーム サーバー) 以外のソースと同期する場合は、サーバーを指定 (IP アドレスを入力します) とポートをこのサーバーはアップ ストリーム サーバーと通信します。  
  
        ![WSUS: WSUS からアップ ストリーム サーバー同期](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4b.png "WSUS_Wiz4b")  
  
    2.  Secure Sockets Layer (SSL) を使用する、**更新プログラムの情報を同期するときに SSL を使用**チェック ボックスをオンします。 その場合は、サーバーは同期のポート 443 を使用します。  
  
        ![WSUS: WSUS SSL からアップ ストリーム サーバー同期](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4c.png "WSUS_Wiz4c")  
  
    3.  レプリカ サーバーの場合は、選択、**これは、アップ ストリーム サーバーのレプリカ**チェック ボックスをオンします。 両方を選択することは**更新情報の同期時に SSL を使用して**と**これは、アップ ストリーム サーバーのレプリカ**します。  
  
        ![WSUS アップ ストリーム サーバーのレプリカ](./media/configure-windows-server-update-services-wsus/WSUS_Wiz4d.png "WSUS_Wiz4d")  
  
    4.  この時点では、アップ ストリーム サーバーの構成が完了したら。 をクリックして**次**、または選択**プロキシ サーバーの指定**左側のナビゲーション ウィンドウで。  
  
5.  プロキシ サーバーを指定します。  
  
    このサーバーには、Microsoft Update へのアクセスにプロキシ サーバーまたは別のアップ ストリーム サーバーが必要とする場合は、ここでは、プロキシ サーバー設定を構成することができます。それ以外の場合、をクリックして**次**します。  
  
    ![WSUS: プロキシ](./media/configure-windows-server-update-services-wsus/WSUS_Wiz5a.png "WSUS_Wiz5a")  
  
    #### <a name="to-configure-proxy-server-settings"></a>プロキシ サーバー設定を構成するには  
  
    1.  **プロキシ サーバーの指定**構成ウィザード のページ、**を同期するときにプロキシ サーバーを使用して**チェック ボックスをオンし、プロキシ サーバーの IP アドレスが (名前ではなく) とポート番号 (ポート 80 で入力既定)、対応するボックスです。  
  
    2.  特定のユーザーの資格情報、選択を使用してプロキシ サーバーに接続する場合、**プロキシ サーバーに接続するユーザーの資格情報を使用して**チェック ボックスをオンし、対応するユーザー名、ドメイン、およびユーザーのパスワードを入力ボックス。 プロキシ サーバーに接続しているユーザーに対して基本認証を有効にする場合、**基本認証を許可する (パスワードはクリア テキストで送信)** チェック ボックスをオンします。  
  
        ![プロキシの資格情報を WSUS](./media/configure-windows-server-update-services-wsus/WSUS_Wiz5b.png "WSUS_Wiz5b")  
  
    3.  この時点では、プロキシ サーバーの構成が完了したら。 をクリックして**次**同期プロセスの設定を開始することができます、次のページに移動します。  
  
6.  接続を開始します。  
  
    ![WSUS: プロキシの接続を開始](./media/configure-windows-server-update-services-wsus/WSUS_Wiz6.png "WSUS_Wiz6")  
  
    クリックして**接続を開始**します。  
  
    接続が成功した後にをクリックして**次**に次のページに移動して、言語を選択できます。  
  
7.  言語を選択します。  
  
    選択**これらの言語でのみ更新プログラムをダウンロード**します。  
  
    選択**英語**、 をクリックし、**次**。  
  
    ![言語の選択](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChooseLanguages.png "SQL_Server_PDW_WSUSChooseLanguages")  
  
8.  製品を選択します。  
  
    > [!NOTE]  
    > アップ ストリーム サーバーを使用している場合、製品の選択することはできません。 このオプションを使用できない場合は、この手順をスキップします。  
  
    選択したすべての更新プログラムをオフにします。  
  
    選択**Windows Server 2012 R2**、および**System Center 2012 R2 の Virtual Machine Manager**、順にクリックします**次**します。  
  
9. 分類を選択します。  
  
    > [!NOTE]  
    > アップ ストリーム サーバーを使用している場合、分類の選択することはできません。  このオプションを使用できない場合は、この手順をスキップします。  
  
    以前に選択したすべての更新プログラムをオフにします。  
  
    選択**重要な更新プログラム**と**セキュリティ更新プログラム**、Analytics Platform System アプライアンスに同期し、更新プログラムの**次**します。  
  
    ![分類の選択](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChooseClassifications.png "SQL_Server_PDW_WSUSChooseClassifications")  
  
10. 同期スケジュールを構成します。  
  
    選択**手動で同期**、順にクリックします**次**します。  
  
    ![同期スケジュールの設定](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSyncSchedule.png "SQL_Server_PDW_WSUSSyncSchedule")  
  
11. 初期同期を開始します。  
  
    選択**初期同期を開始**、 をクリックし、**次**。  
  
12. 終了します。  
  
    **[完了]** をクリックします。  
  
## <a name="bkmk_WSUSGroup"></a>WSUS でアプライアンス サーバーをグループします。  
Analytics Platform System の WSUS を構成した後は、次の手順は、アプライアンス サーバー グループには。 グループには、すべてのアプライアンス サーバーを追加、WSUS は、アプライアンスのすべてのサーバーにソフトウェア更新プログラムを適用することになります。  
  
> [!NOTE]  
> WSUS システムが非同期に実行する設計されています。 アクティビティの開始が常にならない、すぐに更新します。 そのため、コンピューターが WSUS のダイアログ ボックスで表示されますまで、しばらくを待機する必要があります。 実行している、`setup.exe /action=ReportMicrosoftUpdateClientStatus /DomainAdminPassword="<password>"`トピックの最後に記載されているコマンド[ダウンロードと Microsoft 更新プログラムの適用&#40;Analytics Platform System&#41; ](download-and-apply-microsoft-updates.md)  ダイアログ ボックスを更新できます。  
  
#### <a name="to-group-the-appliance-servers"></a>アプライアンス サーバーをグループ化するには  
  
1.  WSUS コンソールを開き、右クリックして**すべてのコンピューター**  をクリックし、**コンピューター グループの追加**します。  
  
    ![コンピューター グループを追加します。](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSAddComputerGroup.png "SQL_Server_PDW_WSUSAddComputerGroup")  
  
2.  コンピューター グループの名前"AP"を入力し、クリックして**追加**します。  
  
    ![新しいコンピューター グループの名前を入力します。](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSpecifyGroupName.png "SQL_Server_PDW_WSUSSpecifyGroupName")  
  
3.  をクリックして**すべてのコンピューター**で状態をもう一度、変更、**状態**ドロップダウン メニューを**任意**、順にクリックします**更新**します。 展開する必要があります**すべてのコンピューター**追加したばかりの新しいグループを表示するには、左側のツリー コントロールでクリックしています。  
  
    ![いずれかの状態を変更し、[更新] をクリックします。](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeStatusToAny.png "SQL_Server_PDW_WSUSChangeStatusToAny")  
  
4.  アプライアンス、右クリックし、クリックの一部であるすべてのコンピューターを選択します。**メンバーシップの変更**します。  
  
    ![すべての PDW コンピューターのメンバーシップを変更します。](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeMembership.png "SQL_Server_PDW_WSUSChangeMembership")  
  
5.  チェック ボックスをクリックし、作成した新しいコンピューター グループの選択**OK**します。  
  
    ![一連のコンピューター グループのメンバーシップ](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSSetComputerGroupMembership.png "SQL_Server_PDW_WSUSSetComputerGroupMembership")  
  
6.  新しいコンピュータ グループを選択し、変更、**状態**に**任意**、順にクリックします**更新**します。 すべてのコンピューターをこのグループに割り当てられているようになりましたと右側のペインに一覧表示する必要があります。 一般に、ノードなどの警告の表示時に続行する安全では**このノードが状態をまだ報告しない**します。  
  
    ![いずれかの状態を変更し、[更新] をクリックします。](./media/configure-windows-server-update-services-wsus/SQL_Server_PDW_WSUSChangeStatusAnyRefresh.png "SQL_Server_PDW_WSUSChangeStatusAnyRefresh")  
  
