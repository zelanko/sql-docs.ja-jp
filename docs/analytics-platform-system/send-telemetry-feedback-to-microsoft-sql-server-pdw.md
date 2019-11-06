---
title: テレメトリのフィードバック - Analytics Platform System |Microsoft Docs
description: Analytics Platform System の Microsoft に製品利用統計情報のフィードバックを送信します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 347879cd468d67b3feee0c92dcd154334df4c237
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960095"
---
# <a name="send-telemetry-feedback-to-microsoft-for-analytics-platform-system"></a>Analytics Platform System のテレメトリのフィードバックをマイクロソフトに送信します。
Analytics Platform System は、管理コンソールのデータを Microsoft に送信する省略可能な製品利用統計情報機能を持ちます。 
  
> [!NOTE]  
> Microsoft が製品利用統計情報データを積極的に監視していないこのリリースでは、です。 分析の目的のみで収集されるデータ。  
  
## <a name="privacy"></a>プライバシー  
最大のプライバシーの保護を提供するには、AP は、テレメトリを有効にしなくても付属しています。 この機能を有効にするには、最初に確認、 [Microsoft Analytics Platform System のプライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=400902)します。 オプトインするには、以下に示す PowerShell スクリプトを実行します。  
  
## <a name="enable"></a>テレメトリを有効にします。  
**DNS の転送:** テレメトリ データを Microsoft に送信するには、DNS フォワーダーを経由してインターネットに接続する Analytics Platform System が必要です。 この機能を有効にするには、すべてのホストと Vm のワークロードに転送する DNS を有効にする必要があります。 呼び出す、`Enable-RemoteMonitoring`コマンドと、`SetupDnsForwarder`適切に DNS の転送を構成し、テレメトリを有効にするにはオプションです。 呼び出す、`Enable-RemoteMonitoring`コマンドを指定せず、 `SetupDnsForwarder` DNS の転送が既に構成されているし、ハートビート監視を有効にするオプションします。  
  
> [!IMPORTANT]  
> DNS の転送を有効にするには、すべてのホストとワークロード Vm のインターネット接続が表示されます。  
  
#### <a name="to-enable-feedback"></a>フィードバックを有効にするには  
  
1.  アプライアンスのドメイン管理者アカウントを使用してコントロールのノードに接続 (<strong>*appliance_domain*-CTL01</strong>) し、Windows 管理者の資格情報を使用してコマンド プロンプトを開きます。  
  
2.  次のディレクトリに移動します:`C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`します。  
  
3.  モジュールをインポートします `Configure-RemoteMonitoring.ps1`  
  
    > [!NOTE]  
    > インポートするには 2 つのピリオドのコマンドを使用する必要があります。  
  
    **例:**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> . .\Configure-RemoteMonitoring.ps1  
    ```  
  
4.  呼び出す、`Enable-RemoteMonitoring`コマンド。  
  
    > [!NOTE]  
    > スクリプトでは、インターネット接続が正しく動作し、インターネット接続を検証しません前提としています。  
  
    1.  初めてのテレメトリを有効にするとは、すべての DNS フォワーダーが正しく構成されていることを確認するのに次のコマンドを使用します。 この例では、DNS 転送された IP アドレスを置き換えます`xx.xx.xx.xx`環境内で DNS フォワーダーの IP アドレスを使用します。  
  
        ```  
        PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Enable-RemoteMonitoring -SetupDnsForwarder -DnsForwarderIp xx.xx.xx.xx  
        ```  
  
    2.  以前に無効に製品利用統計情報を再度有効にするなど、DNS フォワーダーの構成は既に、次のコマンドを使用して DNS の転送を構成せずにテレメトリを有効にします。  
  
        ```  
        PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Enable-RemoteMonitoring  
        ```  
  
5.  読んで AP がアプライアンスに関する情報を収集するかを確認するメッセージが表示されます。 コピーして、確認のための任意のインターネット ブラウザーに貼り付けることができる AP プライバシーに関する声明へのリンクがあります。  
  
6.  入力**Y**を受け入れるとフィードバックすることを選択または入力**N**を受け入れられません。  
  
7.  入力した場合**Y**一連のテレメトリ (および必要に応じて DNS フォワーダー) を有効にするを実行するコマンドがあります、アプライアンス上で機能します。 エラーまたは潜在顧客、コマンドが成功するいないと思われる情報が表示された場合は CSS に問い合わせてしてください。  
  
入力した場合**N**コマンドは実行されませんが何も実行するための詳細およびと機能は有効にされません。  
  
実行しても問題はありません、`Enable-RemoteMonitoring`複数回のコマンドします。 DNS フォワーダーが既に設定されている場合、このようになってを示す警告メッセージが表示されます。  
  
## <a name="disable"></a>テレメトリを無効にします。  
テレメトリを無効にすると、クラウド サービスを監視する APS アプライアンスの状態に関する情報を通信するすべての操作は停止します。  
  
> [!IMPORTANT]  
> DNS フォワーダーまたはアプライアンスの他の機能で使用されている可能性がありますインターネット接続がこの操作は無効にできません。  
  
#### <a name="to-disable-telemetry"></a>テレメトリを無効にするには  
  
1.  アプライアンスのドメイン管理者アカウントを使用してコントロールのノードに接続 (<strong>*appliance_domain*-CTL01</strong>) と、管理者特権で PowerShell ウィンドウを開きます。  
  
2.  次のディレクトリに移動します:`C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`します。  
  
3.  モジュールをインポートします `Configure-RemoteMonitoring.ps1`  
  
    > [!NOTE]  
    > インポートするには 2 つのピリオドのコマンドを使用する必要があります。  
  
    **例:**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> . .\Configure-RemoteMonitoring.ps1  
    ```  
  
4.  呼び出す、`Disable-RemoteMonitoring`パラメーターを指定せずにコマンド。 このコマンドでは、フィードバックの送信を停止します。 (これは影響しませんローカル監視。)ただし、コマンドが DNS フォワーダーを無効にしない、またはインターネット接続を無効にするには。 これは、正常にフィードバックを無効にした後手動で実行する必要があります。  
  
    **例:**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Disable-RemoteMonitoring  
    ```  
  
エラーまたは潜在顧客、コマンドが成功するいないと思われる情報が表示された場合は CSS に問い合わせてしてください。  
  
実行しても問題はありません、`Disable-RemoteMonitoring`複数回のコマンドします。  
  
## <a name="next-steps"></a>次の手順
詳細については、以下をご覧ください。
- [アプライアンスの監視、管理コンソールを使用して&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
- [システム ビューを使用してアプライアンスの監視&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md)  
- [System Center Operations Manager を使用して、アプライアンスの監視&#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
- [非アプライアンス DNS 名を解決するのには、DNS フォワーダーを使用して&#40;Analytics Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
  
