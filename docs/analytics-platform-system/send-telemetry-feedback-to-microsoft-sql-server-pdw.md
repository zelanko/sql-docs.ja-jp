---
title: 製品利用統計情報のフィードバック - Analytics Platform System |Microsoft ドキュメント
description: Analytics Platform System の遠隔測定のフィードバックをマイクロソフトに送信します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 747274cd03e9cbd5dd2eab4423458700331358dd
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31539502"
---
# <a name="send-telemetry-feedback-to-microsoft-for-analytics-platform-system"></a>Analytics Platform System の遠隔測定のフィードバックをマイクロソフトに送信します。
Analytics Platform System が、管理コンソールのデータを Microsoft に送信する省略可能な製品利用統計情報の機能です。 
  
> [!NOTE]  
> このリリースで Microsoft が積極的に監視していない遠隔測定データ。 分析用にのみ、データは収集されています。  
  
## <a name="privacy"></a>プライバシー  
最大のプライバシー保護を提供するには、遠隔測定を有効にせず APS が同梱されています。 この機能を有効にする前に確認最初、 [Microsoft Analytics Platform System のプライバシーに関する声明](http://go.microsoft.com/fwlink/?LinkId=400902)です。 オプトインには、次に示す PowerShell スクリプトを実行します。  
  
## <a name="enable"></a>遠隔測定を有効にします。  
**DNS の転送:** DNS フォワーダーを経由してインターネットに接続する Analytics Platform System 遠隔測定データを Microsoft に送信する必要があります。 この機能を有効にするには、すべてのホストと仮想マシンのワークロードで転送する DNS を有効にする必要があります。 呼び出す、`Enable-RemoteMonitoring`コマンドと、`SetupDnsForwarder`正しく DNS の転送を構成し、製品利用統計情報を有効にするにはオプションです。 呼び出す、`Enable-RemoteMonitoring`コマンドは使用せず、 `SetupDnsForwarder` DNS の転送が既に構成されているし、ハートビート監視を有効にするオプションを選択します。  
  
> [!IMPORTANT]  
> DNS の転送を有効にするには、すべてのホストとワークロード Vm のインターネット接続が表示されます。  
  
#### <a name="to-enable-feedback"></a>フィードバックを有効にするには  
  
1.  アプライアンス ドメインの管理者アカウントを使用してコントロールのノードに接続 (***appliance_domain *-CTL01**) し、Windows 管理者の資格情報を使用してコマンド プロンプトを開きます。  
  
2.  次のディレクトリに移動:`C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`です。  
  
3.  モジュールをインポートします。 `Configure-RemoteMonitoring.ps1`  
  
    > [!NOTE]  
    > インポートするには、必要があります 2 つのピリオド コマンド内で使用します。  
  
    **例:**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> . .\Configure-RemoteMonitoring.ps1  
    ```  
  
4.  呼び出す、`Enable-RemoteMonitoring`コマンド。  
  
    > [!NOTE]  
    > スクリプトでは、インターネット接続が正しく動作し、インターネット接続を検証しません前提としています。  
  
    1.  初めて、遠隔測定を有効にするでは、次のコマンドを使用して、すべての DNS フォワーダーが正しく構成されていることを確認します。 この例では、DNS 転送された IP アドレスを置き換える`xx.xx.xx.xx`環境内で DNS フォワーダーの IP アドレスを使用します。  
  
        ```  
        PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Enable-RemoteMonitoring -SetupDnsForwarder -DnsForwarderIp xx.xx.xx.xx  
        ```  
  
    2.  DNS フォワーダーが既に構成されている場合、製品利用統計情報を再度有効に以前に無効にするなど、DNS 転送を構成しなくても遠隔測定を有効にする、次のコマンドを使用します。  
  
        ```  
        PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Enable-RemoteMonitoring  
        ```  
  
5.  読み取りおよび APS がアプライアンスに関する情報を収集する確認を求められます。 コピーし、確認用の任意のインターネット ブラウザーに貼り付けることができる AP プライバシーに関する声明へのリンクがあります。  
  
6.  入力**Y**を受け入れるとフィードバックをオプトインまたは入力して**N**を受け付けないようにします。  
  
7.  入力した場合**Y**一連の遠隔測定 (および必要に応じて DNS フォワーダー) が有効になりますが実行されるコマンドがあります、アプライアンスで機能します。 いずれかのエラーまたはすると、コマンドが失敗したことと考えられる潜在顧客の情報を表示する場合は、CSS に問い合わせてください。  
  
入力した場合**N**コマンドは実行されませんが何も操作するための詳細およびして、機能が無効です。  
  
実行中で害はありません、`Enable-RemoteMonitoring`コマンドを複数回です。 DNS フォワーダーが既に設定されている場合は、そのようなことを示す警告メッセージが表示されます。  
  
## <a name="disable"></a>製品利用統計情報を無効にします。  
製品利用統計情報を無効にすると、クラウド サービスを監視する APS アプライアンスの状態に関する情報を伝達するすべての操作は停止します。  
  
> [!IMPORTANT]  
> DNS フォワーダまたはアプライアンス内の他の機能によって使用されている可能性がありますインターネット接続がこの操作の実行は無効にできません。  
  
#### <a name="to-disable-telemetry"></a>製品利用統計情報を無効にするには  
  
1.  アプライアンス ドメインの管理者アカウントを使用してコントロールのノードに接続 (***appliance_domain *-CTL01**) し、管理者特権で PowerShell ウィンドウを開きます。  
  
2.  次のディレクトリに移動:`C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`です。  
  
3.  モジュールをインポートします。 `Configure-RemoteMonitoring.ps1`  
  
    > [!NOTE]  
    > インポートするには、必要があります 2 つのピリオド コマンド内で使用します。  
  
    **例:**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> . .\Configure-RemoteMonitoring.ps1  
    ```  
  
4.  呼び出す、`Disable-RemoteMonitoring`パラメーターを指定せずにコマンド。 このコマンドでは、フィードバックの送信を停止します。 (これは影響しませんローカルの監視。)ただし、コマンドはいない DNS フォワーダーを無効にするか、またはすべてのインターネット接続を無効にします。 これは、正常にフィードバックを無効にした後手動で行う必要があります。  
  
    **例:**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Disable-RemoteMonitoring  
    ```  
  
いずれかのエラーまたはすると、コマンドが失敗したことと考えられる潜在顧客の情報を表示する場合は、CSS に問い合わせてください。  
  
実行中で害はありません、`Disable-RemoteMonitoring`コマンドを複数回です。  
  
## <a name="next-steps"></a>次の手順
詳細については、以下をご覧ください。
- [管理者コンソールを使用してアプライアンスをモニター&#40;分析プラットフォーム システム&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
- [システム ビューを使用してアプライアンスをモニター&#40;分析プラットフォーム システム&#41;](monitor-the-appliance-by-using-system-views.md)  
- [System Center Operations Manager を使用してアプライアンスを監視する&#40;分析プラットフォーム システム&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
- [非アプライアンスの DNS 名を解決するのには、DNS フォワーダーを使用して&#40;分析プラットフォーム システム&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
  
