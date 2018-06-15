---
title: Microsoft Updates - Analytics Platform System のダウンロード |Microsoft ドキュメント
description: このトピックでは、Windows Server Update Services (WSUS) を Microsoft Update カタログから更新プログラムをダウンロードし、Analytics Platform System アプライアンス サーバーにそれらの更新プログラムを適用する方法について説明します。 Microsoft Update は Windows および SQL Server のすべての該当する更新プログラムをインストールします。 WSUS は、アプライアンスの VMM 仮想マシンにインストールされます。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: b98a2be90f222fc2c531c1f1983f8882bdab640e
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31539522"
---
# <a name="download-and-apply-microsoft-updates-for-analytics-platform-system"></a>ダウンロードし、Analytics Platform System の Microsoft 更新プログラムを適用
このトピックでは、Windows Server Update Services (WSUS) を Microsoft Update カタログから更新プログラムをダウンロードし、Analytics Platform System アプライアンス サーバーにそれらの更新プログラムを適用する方法について説明します。 Microsoft Update は Windows および SQL Server のすべての該当する更新プログラムをインストールします。 WSUS は、アプライアンスの VMM 仮想マシンにインストールされます。  
  
## <a name="TOP"></a>はじめに  
  
> [!WARNING]  
> アプライアンスまたはアプライアンス コンポーネントがダウンしているか、エラー状態の場合は、更新プログラムを適用しないでの状態の上です。 その場合は、サポートが必要なサポートに問い合わせてください。  
>   
> アプライアンスの使用中に Microsoft 更新プログラムは適用されません。 更新プログラムを適用すると、アプライアンスのノードを再起動する可能性があります。 アプライアンスが使用されていないときに、メンテナンス期間中に、更新を適用する必要があります。  
  
### <a name="prerequisites"></a>前提条件  
次の手順を実行する前にする必要があります。  
  
-   アプライアンス上の指示に従いして WSUS を構成[Windows Server Update Services の構成&#40;WSUS&#41; &#40;Analytics Platform System&#41;](configure-windows-server-update-services-wsus.md)です。  
  
-   ファブリック管理者はドメイン アカウントのログイン情報のナレッジ。  
  
-   分析プラットフォーム システム管理コンソールにアクセスし、アプライアンスの状態情報を表示する権限を持つログインを持っています。  
  
-   ほとんどの場合、WSUS は、アプライアンスの外部のサーバーにアクセスする必要があります。 外部名を解決するのには外部 DNS サーバーを使用するには、Analytics Platform System ホストとバーチャル マシン (Vm) を許可する外部名転送をサポートするために分析プラットフォーム システム DNS を構成することができます、この使用シナリオをサポートするために、アプライアンスです。 詳細については、次を参照してください。[非アプライアンス DNS 名の解決に DNS フォワーダーを使用して&#40;Analytics Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)です。  
  
## <a name="bkmk_ImportUpdates"></a>ダウンロードして、Microsoft 更新プログラムを適用するには  
  
#### <a name="verify-the-appliance-state-indicators"></a>アプライアンスの状態インジケーターを確認してください。  
  
1.  管理コンソールを開き、アプライアンスの状態 ページに移動します。 詳細については、次を参照してください[アプライアンスを管理コンソールを使用して監視&#40;分析プラットフォーム システム。&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
2.  アプライアンスの状態は、上のすべてのノードのステータス インジケーターを確認します。  
  
    -   緑または NA インジケーターを続行する安全です。  
  
    -   重大でない (黄色) 警告エラーを評価します。 場合によっては警告メッセージには 更新プログラムはブロックされません。 C:\ ドライブにないに重大でないディスク ボリューム エラーがある場合、ディスク ボリュームのエラーを解決する前に、次の手順を続行することができます。  
  
    -   ほとんどの赤のインジケーターは、続行する前に解決する必要があります。 ディスクの障害がある場合は、管理者コンソール [アラート] ページを使用して、各サーバーまたは SAN 配列内の 2 つ以上のディスク障害が発生したことを確認します。 各サーバーまたは SAN 配列内の 2 つ以上のディスク障害がある場合、ディスク エラーを修正する前に、次の手順を続行することができます。 ディスクの障害をできるだけ早く修正を Microsoft サポートに問い合わせることを確認します。  
  
#### <a name="synchronize-the-wsus-server"></a>WSUS サーバーを同期します。  
  
1.  VMM バーチャル マシンにドメイン管理者としてログオンします。  
  
2.  **サーバー マネージャー ダッシュ ボード**の**ツール** メニューのをクリックして**Windows Server Update Services** (**wsus.msc**)。  
  
3.  WSUS 管理コンソールで、をクリックして**同期**です。  
  
4.  同期が実行されていない場合はクリックして**今すぐ同期**右側のウィンドウでします。 下のペインで、同期の状態があります。 同期が完了するまで待機します。  
  
#### <a name="approve-microsoft-updates-in-wsus"></a>WSUS での Microsoft 更新プログラムを承認します。  
  
1.  クリックして、WSUS コンソールの左側で**更新プログラムをすべて**です。  
  
2.  **すべての更新プログラム** ウィンドウで、をクリックして、**承認**設定し、ドロップダウン メニュー**承認**に**辞退を除く任意**です。 をクリックして、**ステータス**設定し、ドロップダウン メニュー**ステータス**に**任意**です。 **[更新]** をクリックします。  
  
    右クリックし、**タイトル**列を選択**ファイルの状態の**をダウンロードが完了した後、ファイルの状態を確認します。  
  
    選択することも**重要な更新プログラム**または**セキュリティ更新プログラム**でこれらのカテゴリの左側のウィンドウとビュー利用可能な更新します。  
  
    ![すべての更新プログラムを選択し、いずれかの状態を変更します。] (./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectAllUpdates.png "SQL_Server_PDW_WSUSSelectAllUpdates")  
  
3.  すべての更新プログラムを選択し、クリックして、**承認**右側のウィンドウでリンクします。  
  
    また、選択した更新プログラムを右クリックしてをクリックして**承認**です。 "Microsoft ソフトウェア ライセンス条項に同意"を求められる場合があります。 場合は、クリックして**同意**続行する ウィンドウでします。  
  
    ![[承認] をクリックしておよび適用されるすべての更新プログラムを選択します。] (./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectApprove.png "SQL_Server_PDW_WSUSSelectApprove")  
  
4.  作成したアプライアンス サーバー グループを選択して[Windows Server Update Services の構成&#40;WSUS&#41; &#40;Analytics Platform System&#41;](configure-windows-server-update-services-wsus.md)です。  
  
5.  をクリックして**インストールの承認**、順にクリック**OK**です。  
  
    ![コンピューター グループの更新プログラムを承認します。] (./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectApprovalType.png "SQL_Server_PDW_WSUSSelectApprovalType")  
  
6.  **承認の進行状況**ダイアログ ボックスで、承認プロセスが完了したら、をクリックして**閉じる**です。  
  
    ![更新プログラムが承認されると、ウィンドウを閉じます。] (./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSCloseApprovalProgressWindow.png "SQL_Server_PDW_WSUSCloseApprovalProgressWindow")  
  
#### <a name="verify-that-the-updates-are-in-wsus"></a>WSUS で更新があることを確認してください。  
  
-  すべての更新プログラムのファイルの状態を確認します。 各ファイルには、タイトルの左側の緑色の矢印アイコンが必要です。 これは、ファイルがインストールの準備ができてを示します。  
  
    ![ファイルの状態が成功した](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUS_File_Status.png "SQL_Server_PDW_WSUS_File_Status")  
  
    更新プログラムをインストールする前にすべてダウンロードして、WSUS コンソールで使用されることを確認します。  
  
#### <a name="to-verify-that-all-updates-are-downloaded"></a>すべての更新プログラムがダウンロードしたことを確認するには  
  
-  チェック、**ダウンロード ステータス**次のスクリーン ショットに示すように、WSUS コンソールでの更新。 確認**ファイルを必要とする更新プログラム**は、すべての更新プログラムをダウンロードすることを確認する場合は 0 です。 この数値がゼロより大きい場合は、戻っておよび追加の更新プログラムを承認する必要があります。  
  
    ![すべての更新プログラムがダウンロードしたことを確認します。] (./media/download-and-apply-microsoft-updates/SQL_Server_PDS_WSUS_VerifyDownloadUpdateJPG.png "SQL_Server_PDS_WSUS_VerifyDownloadUpdateJPG")  
  
#### <a name="apply-microsoft-updates"></a>Microsoft 更新プログラムを適用します。  
  
1.  開始する前に開く、[アプライアンスを管理コンソールを使用して監視&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)をクリックして、**のアプライアンス状態**タブをクリックし、いることを確認、 **クラスター**と**ネットワーク**列緑の表示 (NA) のすべてのノードです。 すべてのアラートは、これらの列のいずれかに存在する場合、アプライアンスできないことがありますの更新プログラムを正常にインストールします。 内の既存のすべてのアラートに対処、**クラスター**と**ネットワーク**続行する前に列です。  
  
2.  ログオン、 *< domain_name > * * *-HST01** ファブリック ドメイン管理者としてのノードです。  
  
3.  すべての更新プログラムが WSUS の承認を適用するには、更新プログラムを実行します。 参照してください[更新プログラムを実行](#RunUpdateWizard)下手順についてはします。  
  
#### <a name="verify-the-updates-on-all-nodes"></a>すべてのノードで更新プログラムを確認してください。  
  
1.  VMM のノードから、WSUS 管理コンソールを起動します。 このアプリケーションは「**開始**、**管理ツール**、 **Windows Server Update Services**です。  
  
2.  展開**コンピューター**です。  
  
3.  展開**すべてのコンピューター**です。  
  
4.  作成したアプライアンス サーバー グループを選択して[Windows Server Update Services の構成&#40;WSUS&#41; &#40;Analytics Platform System&#41;](configure-windows-server-update-services-wsus.md)です。  
  
5.  **ステータス**ドロップダウン メニューで、**任意** をクリック**更新**です。  
  
6.  展開**サービス更新**、 *<appliance name>* VMM、**更新**、**すべての更新プログラム**ここで、  *<appliance name>* アプライアンスの名前を指定します。  
  
7.  **更新プログラムをすべて**ウィンドウ セット**承認**に**辞退を除く任意**です。  
  
8.  **更新プログラムをすべて**ウィンドウで、設定**ステータス**に**失敗、または必要**です。  
  
9. **[更新]** をクリックします。  
  
10. 場合**必要な更新プログラム**がゼロ、連絡先のサポートにお問い合わせより大きい。  
  
#### <a name="ensure-there-are-no-critical-alerts-in-the-sql-server-pdw-admin-console"></a>SQL Server PDW 管理コンソールに重大なアラートがないことを確認します。  
  
1.  管理コンソールを開き、アプライアンスの状態 タブをクリックします。参照してください[アプライアンスを管理コンソールを使用して監視&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)です。  
  
2.  いることを確認、**クラスター**と**ネットワーク**列緑の表示 (NA) のすべてのノードです。 すべてのアラートは、これらの列のいずれかに存在する場合、アプライアンスできないことがありますの更新プログラムを正常にインストールします。 重大なアラートがある場合、サポートに問い合わせてください。  
  
## <a name="RunUpdateWizard"></a>更新プログラムを実行します。  
分析プラットフォーム システム更新プログラムを実行する手順に従います。  
  
> [!NOTE]  
> WSUS システムするものでは実行に非同期的に時間がかかる場合に、すべての更新プログラムを完全に適用します。 更新プログラムを開始していますが、更新をスケジュール、即時更新アクティビティとは限りません。  
  
1.  HST01 ノード ファブリック ドメイン管理者としてログインしていることを確認してください。  
  
2.  コマンド プロンプト ウィンドウを開き、次のコマンドを入力します。 置き換える*<parameter>* 指定された情報を使用します。  
  
**Microsoft Update を実行します。**  
  
```  
C:\pdwinst\media\setup.exe /action="MicrosoftUpdate" /DomainAdminPassword="<password>"  
```  
  
**Microsoft Update のステータスを報告します。**  
  
```  
C:\pdwinst\media\setup.exe /action="ReportMicrosoftUpdateClientStatus" /DomainAdminPassword="<password>"  
```  
  
## <a name="see-also"></a>参照  
[Microsoft 更新プログラムのアンインストール&#40;分析プラットフォーム システム&#41;](uninstall-microsoft-updates.md)  
[分析プラットフォーム システムの修正プログラム適用&#40;分析プラットフォーム システム&#41;](apply-analytics-platform-system-hotfixes.md)  
[分析プラットフォーム システムの修正プログラムをアンインストール&#40;分析プラットフォーム システム&#41;](uninstall-analytics-platform-system-hotfixes.md)  
[ソフトウェア サービス&#40;分析プラットフォーム システム&#41;](software-servicing.md)  
  
