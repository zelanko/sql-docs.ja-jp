---
title: Microsoft Updates - Analytics Platform System のダウンロード |Microsoft Docs
description: このトピックでは、Windows Server Update Services (WSUS) を Microsoft Update カタログから更新プログラムをダウンロードして、Analytics Platform System appliance のサーバーにこれらの更新プログラムを適用する方法について説明します。 Microsoft Update は Windows と SQL Server のすべての該当する更新プログラムをインストールします。 WSUS は、アプライアンスの VMM のバーチャル マシンにインストールされます。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 78da7bd46282bb42bc3630c71c1cafd1ea0f11bc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67961045"
---
# <a name="download-and-apply-microsoft-updates-for-analytics-platform-system"></a>ダウンロードおよび Analytics Platform System の Microsoft 更新プログラムを適用
このトピックでは、Windows Server Update Services (WSUS) を Microsoft Update カタログから更新プログラムをダウンロードして、Analytics Platform System appliance のサーバーにこれらの更新プログラムを適用する方法について説明します。 Microsoft Update は Windows と SQL Server のすべての該当する更新プログラムをインストールします。 WSUS は、アプライアンスの VMM のバーチャル マシンにインストールされます。  
  
## <a name="TOP"></a>はじめに  
  
> [!WARNING]  
> アプライアンスまたはアプライアンス コンポーネントがダウンしているかで、失敗した場合は、更新プログラムを適用しないで状態にします。 その場合は、についてサポートに問い合わせてください。  
>   
> アプライアンスを使用中に Microsoft 更新プログラムは適用されません。 更新プログラムを適用すると、アプライアンスのノードを再起動する可能性があります。 アプライアンスが使用されていないときに、メンテナンス期間中に、更新プログラムを適用する必要があります。  
  
### <a name="prerequisites"></a>前提条件  
次の手順を実行する前にする必要があります。  
  
-   次の手順でアプライアンス上の WSUS を構成する[Windows Server Update Services の構成&#40;WSUS&#41; &#40;Analytics Platform System&#41;](configure-windows-server-update-services-wsus.md)します。  
  
-   ファブリック管理者はドメイン アカウントのログイン情報の知識。  
  
-   Analytics Platform System の管理コンソールにアクセスし、アプライアンスの状態情報を表示する権限を持つログインがあります。  
  
-   ほとんどの場合、WSUS は、アプライアンスの外部にあるサーバーにアクセスする必要があります。 外部名を解決するのには、外部の DNS サーバーを使用するには、Analytics Platform System のホストと仮想マシン (Vm) を許可する外部名転送をサポートするために、分析プラットフォーム システム DNS を構成できますこの使用シナリオをサポートするために、アプライアンスです。 詳細については、次を参照してください。[非アプライアンス DNS 名の解決に DNS フォワーダーを使用して、 &#40;Analytics Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)します。  
  
## <a name="bkmk_ImportUpdates"></a>ダウンロードして、Microsoft 更新プログラムを適用するには  
  
#### <a name="verify-the-appliance-state-indicators"></a>アプライアンスの状態インジケーターを確認します。  
  
1.  管理コンソールを開き、アプライアンスの状態 ページに移動します。 詳細については、次を参照してください[アプライアンスの監視、管理コンソールを使用して&#40;Analytics Platform System。&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
  
2.  アプライアンスの状態は、すべてのノードの状態インジケーターを確認します。  
  
    -   緑または NA インジケーターを続行しても安全になります。  
  
    -   重大でない (黄色) 警告エラーを評価します。 場合によっては警告メッセージには 更新プログラムはブロックされません。 C:\ ドライブではないに重大でないディスク ボリューム エラーがある場合、ディスク ボリュームのエラーを解決する前に、次の手順に進むことができます。  
  
    -   ほとんどの赤のインジケーターは、続行する前に解決する必要があります。 ディスク障害がある場合は、管理者コンソール [アラート] ページを使用して、各サーバーまたは SAN 配列内で複数のディスク障害が発生したことを確認します。 各サーバーまたは SAN 配列内の複数のディスク障害がある場合、ディスク エラーを修正する前に、次の手順に進むことができます。 できるだけ早くディスク障害を解決する Microsoft サポートに連絡してください。  
  
#### <a name="synchronize-the-wsus-server"></a>WSUS サーバーを同期します。  
  
1.  ドメイン管理者として VMM のバーチャル マシンにログオンします。  
  
2.  **サーバー マネージャー ダッシュ ボード**の**ツール** メニューのをクリックして**Windows Server Update Services** (**wsus.msc**)。  
  
3.  WSUS 管理コンソールで、クリックして**同期**します。  
  
4.  同期が実行されていない場合はクリックして**今すぐ同期**右側のペインでします。 下のペインで、同期の状態があります。 同期が完了するまで待機します。  
  
#### <a name="approve-microsoft-updates-in-wsus"></a>WSUS での Microsoft 更新プログラムを承認します。  
  
1.  WSUS コンソールの左側のウィンドウで次のようにクリックします。**すべての更新プログラム**します。  
  
2.  **すべての更新プログラム**ウィンドウで、をクリックして、**承認**ドロップダウン メニューから、セット**承認**に**拒否を除く任意**します。 をクリックして、**状態**ドロップダウン メニューから、セット**状態**に**任意**します。 **[更新]** をクリックします。  
  
    右クリックし、**タイトル**列と select**ファイルの状態**ダウンロードが完了した後、ファイルの状態を確認します。  
  
    選択することも**重要な更新プログラム**または**セキュリティ更新プログラム**でこれらのカテゴリの左側のウィンドウとビュー利用可能な更新します。  
  
    ![すべての更新プログラムを選択し、いずれかの状態を変更します。](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectAllUpdates.png "SQL_Server_PDW_WSUSSelectAllUpdates")  
  
3.  すべての更新プログラムを選択し、クリックして、**承認**右側のウィンドウでリンクします。  
  
    右クリックしても、選択した更新プログラムをクリックしたことができます**承認**します。 「Microsoft ソフトウェア ライセンス条項」に同意を求めるメッセージが表示可能性があります。 そうである場合は、クリックして**同意**続行する ウィンドウでします。  
  
    ![[承認] をクリックして、適用されるすべての更新プログラムを選択します。](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectApprove.png "SQL_Server_PDW_WSUSSelectApprove")  
  
4.  作成したアプライアンス サーバー グループを選択[Windows Server Update Services の構成&#40;WSUS&#41; &#40;Analytics Platform System&#41;](configure-windows-server-update-services-wsus.md)します。  
  
5.  クリックして**インストールの承認**、順にクリックします**OK**します。  
  
    ![コンピューター グループの更新プログラムを承認します。](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSSelectApprovalType.png "SQL_Server_PDW_WSUSSelectApprovalType")  
  
6.  **承認の進行状況** ダイアログ ボックスで、承認プロセスが完了したら、をクリックして**閉じる**します。  
  
    ![更新プログラムが承認されたときにウィンドウを閉じます。](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUSCloseApprovalProgressWindow.png "SQL_Server_PDW_WSUSCloseApprovalProgressWindow")  
  
#### <a name="verify-that-the-updates-are-in-wsus"></a>WSUS で更新があることを確認します。  
  
-  すべての更新プログラムのファイルの状態を確認します。 各ファイルには、タイトルの左側に緑色の矢印アイコンが必要です。 これは、ファイルがインストールできる状態を示します。  
  
    ![ファイルの状態が成功した](./media/download-and-apply-microsoft-updates/SQL_Server_PDW_WSUS_File_Status.png "SQL_Server_PDW_WSUS_File_Status")  
  
    更新プログラムをインストールする前にすべてダウンロードして、WSUS コンソールで使用されることを確認します。  
  
#### <a name="to-verify-that-all-updates-are-downloaded"></a>すべての更新プログラムがダウンロードされたことを確認するには  
  
-  チェック、**ダウンロード ステータス**の次のスクリーン ショットに示すように、WSUS コンソールで、更新プログラム。 いることを確認**ファイルを必要とする更新プログラム**はすべての更新プログラムがダウンロードされることを確認するには 0。 この数値がゼロより大きい場合は、追加の更新プログラムを承認する必要があります。  
  
    ![すべての更新プログラムをダウンロードすることを確認します。](./media/download-and-apply-microsoft-updates/SQL_Server_PDS_WSUS_VerifyDownloadUpdateJPG.png "SQL_Server_PDS_WSUS_VerifyDownloadUpdateJPG")  
  
#### <a name="apply-microsoft-updates"></a>Microsoft 更新プログラムを適用します。  
  
1.  開始する前に開いて、[アプライアンスの監視、管理コンソールを使用して&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)、 をクリックして、**アプライアンスの状態は**タブをクリックし、いることを確認、 **クラスター**と**ネットワーク**列緑色の表示 (NA) のすべてのノード。 すべてのアラートは、これらの列のいずれかに存在する場合、アプライアンスは正常に更新プログラムをインストールできる可能性がありますいないです。 既存のすべてのアラートに対処、**クラスター**と**ネットワーク**続行する前に列。  
  
2.  ログオン、 _< domain_name >_ **-HST01** Fabric ドメイン管理者としてのノード。  
  
3.  WSUS が承認されたすべての更新を適用するには、更新プログラムを実行します。 参照してください[更新プログラムを実行](#RunUpdateWizard)以下の手順についてはします。  
  
#### <a name="verify-the-updates-on-all-nodes"></a>すべてのノードで更新プログラムを確認します。  
  
1.  VMM のノードから、WSUS 管理コンソールを起動します。 このアプリケーションは、「**開始**、**管理ツール**、 **Windows Server Update Services**します。  
  
2.  展開**コンピューター**します。  
  
3.  展開**すべてのコンピューター**します。  
  
4.  作成したアプライアンス サーバー グループを選択[Windows Server Update Services の構成&#40;WSUS&#41; &#40;Analytics Platform System&#41;](configure-windows-server-update-services-wsus.md)します。  
  
5.  **状態**ドロップダウン メニューで、**任意**クリック**更新**。  
  
6.  展開**サービス更新**、 *<appliance name>* - VMM では、**更新**、**すべての更新プログラム**ここで、  *<appliance name>* アプライアンスの名前を指定します。  
  
7.  **すべての更新プログラム**ウィンドウ セット**承認**に**拒否を除く任意**します。  
  
8.  **すべての更新プログラム**ウィンドウで、設定**状態**に**が失敗したか、必要な**します。  
  
9. **[更新]** をクリックします。  
  
10. 場合**に必要な更新**が 0 個、連絡先のサポートにお問い合わせより大きい。  
  
#### <a name="ensure-there-are-no-critical-alerts-in-the-sql-server-pdw-admin-console"></a>SQL Server PDW 管理コンソールに重大なアラートがないことを確認します。  
  
1.  管理者コンソールを開き、アプライアンスの状態 タブをクリックします。参照してください[アプライアンスの監視、管理コンソールを使用して&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)します。  
  
2.  いることを確認、**クラスター**と**ネットワーク**列緑色の表示 (NA) のすべてのノード。 すべてのアラートは、これらの列のいずれかに存在する場合、アプライアンスは正常に更新プログラムをインストールできる可能性がありますいないです。 重大なアラートがある場合は、サポートにお問い合わせください。  
  
## <a name="RunUpdateWizard"></a>更新プログラムを実行します。  
この手順では、Analytics Platform System の更新プログラムを実行します。  
  
> [!NOTE]  
> WSUS のシステムの実行は非同期的にすべての更新プログラムを完全に適用するまでに時間をかかる場合があります。 更新プログラムを開始していますが、更新プログラムをスケジュール、即時更新アクティビティとは限りません。  
  
1.  HST01 ノード Fabric ドメイン管理者としてログインしていることを確認します。  
  
2.  コマンド プロンプト ウィンドウを開き、次のコマンドを入力します。 置換 *<parameter>* 指定された情報を使用します。  
  
**Microsoft Update を実行します。**  
  
```  
C:\pdwinst\media\setup.exe /action="MicrosoftUpdate" /DomainAdminPassword="<password>"  
```  
  
**Microsoft 更新プログラムの状態を報告するには。**  
  
```  
C:\pdwinst\media\setup.exe /action="ReportMicrosoftUpdateClientStatus" /DomainAdminPassword="<password>"  
```  
  
## <a name="see-also"></a>参照  
[Microsoft 更新プログラムのアンインストール&#40;Analytics Platform System&#41;](uninstall-microsoft-updates.md)  
[Analytics Platform System の修正プログラムを適用&#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
[Analytics Platform System の修正プログラムのアンインストール&#40;Analytics Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
[ソフトウェアのサービス&#40;Analytics Platform System&#41;](software-servicing.md)  
  
