---
title: SQL Server ユーティリティのトラブルシューティング |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f5f47c2a-38ea-40f8-9767-9bc138d14453
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0bc94d8644d1a0015829b730d5556b967c6b8c93
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084158"
---
# <a name="troubleshoot-the-sql-server-utility"></a>SQL Server ユーティリティのトラブルシューティング
  ph x="1" /&gt; ユーティリティのトラブルシューティングの項目としては、UCP を使用した SQL Server インスタンスの登録処理の失敗の解決、データ収集の失敗 (UCP のマネージド インスタンスのリスト ビューで灰色のアイコンが表示される) に対するトラブルシューティング、パフォーマンス ボトルネックの緩和、リソースの正常性に関する問題の解決などがあります。 によって識別されるリソース正常性の問題を緩和する方法について、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] UCP を参照してください[SQL Server リソース正常性をトラブルシューティング&#40;SQL Server ユーティリティ&#41;](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md)です。  
  
## <a name="failed-operation-to-enroll-an-instance-of-sql-server-into-a-sql-server-utility"></a>SQL Server インスタンスを SQL Server ユーティリティに登録する処理の失敗  
 インスタンスに接続する場合[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]を使用して登録[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]認証、および UCP があるドメインとは異なる Active Directory ドメインに属するプロキシ アカウントを指定するインスタンスの検証が成功したが、登録操作は、次のエラー メッセージで失敗します。  
  
 Transact-SQL ステートメントまたはバッチの実行中に例外が発生しました。 (Microsoft.SqlServer.ConnectionInfo)  
  
 追加情報: Windows NT グループまたはユーザー '\<ドメイン名\アカウント名>' に関する情報を取得できませんでした。エラー コード 0x5。 (Microsoft SQL Server、エラー: 15404)  
  
 この問題は、次のようなシナリオで発生します。  
  
1.  UCP は "Domain_1" のメンバーです。  
  
2.  一方向のドメイン信頼関係が存在します。つまり、"Domain_1" は "Domain_2" から信頼されていませんが、"Domain_2" は "Domain_1" から信頼されています。  
  
3.  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティに登録する [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスは、"Domain_1" のメンバーでもあります。  
  
4.  登録処理中に、登録する [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに "sa" を使用して接続します。 "Domain_2" からのプロキシ アカウントを指定します。  
  
5.  検証に成功しますが、登録に失敗します。  
  
 この問題を回避するには、上の例の場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティに登録する [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに "sa" を使用して接続し、"Domain_1" からのプロキシ アカウントを指定します。  
  
## <a name="failed-wmi-validation"></a>WMI 検証の失敗  
 ph x="1" /&gt; インスタンスで WMI が正しく構成されていない場合は、UCP の作成操作とマネージド インスタンスの登録操作で警告が表示されますが、操作はブロックされません。 さらに、変更した場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]エージェント アカウントの構成できるように[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]エージェントに必要な WMI クラスの影響を受けるマネージ インスタンス上のデータ収集するアクセス許可がない[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]UCP へのアップロードに失敗します。 この結果、UCP に灰色のアイコンが表示されます。  
  
 データ収集が失敗した結果、影響を受ける [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のマネージド インスタンスの UCP リスト ビューに灰色の状態アイコンが表示されます。 ph x="1" /&gt; のマネージド インスタンスのジョブ履歴には、sysutility_mi_collect_and_upload がステップ 2 (PowerShell スクリプトから収集されたデータのステージング) で失敗したことが示されます。  
  
 エラー メッセージの要約は次のとおりです。  
  
 シェル変数 "ErrorActionPreference" が Stop に設定されているため、コマンドの実行が停止しました: アクセスが拒否されました。  
  
 エラー:\<日時 (/MM/DD/YYYY HH:MM:SS) >: cpu プロパティの収集中に例外をキャッチします。  WMI クエリに失敗した可能性があります。  警告。  
  
 この問題を解決するには、次の構成設定を確認します。  
  
-   SQL Server エージェント サービス Windows Server 2003 でのマネージ インスタンス上の Windows Performance Monitoring グループの一部である必要があります[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]です。  
  
-   ph x="1" /&gt; のマネージド インスタンス上で、WMI サービスが有効になっており、構成されている必要があります。  
  
-   WMI リポジトリのマネージ インスタンスで破損している場合があります[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]です。  
  
-   パフォーマンス ライブラリには、不足しているかのマネージ インスタンスで壊れている可能性があります[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]です。  
  
 指定した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスが UCP にデータを報告するように正しく構成されていることを検証するには、指定した [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスで次のクラスが使用可能であり、SQL Server エージェント サービス アカウントからこれらのクラスにアクセスできるかどうかを確認します。  
  
-   Win32_MountPoint  
  
-   Win32_PerfRawData_PerfProc_Process  
  
-   Win32_PerfRawData_PerfOS_Processor  
  
-   Win32_Processor  
  
-   Win32_Volume  
  
-   Win32_LogicalDisk  
  
 各クラスで Get-WmiObject PowerShell コマンドレットを使用して、各クラスにアクセスできるかどうかを確認します。 マネージ インスタンスで、次のコマンドレットを実行[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:  
  
```  
Get-WmiObject Win32_MountPoint -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_PerfRawData_PerfProc_Process -ErrorAction Stop| Out-Null  
Get-WmiObject Win32_PerfRawData_PerfOS_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Processor -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_Volume -ErrorAction Stop | Out-Null  
Get-WmiObject Win32_LogicalDisk -ErrorAction Stop | Out-Null  
```  
  
 WMI のトラブルシューティングの詳細については、次を参照してください。 [WMI のトラブルシューティング](http://go.microsoft.com/fwlink/?LinkId=178250)です。 SQL Server ユーティリティのこれらの操作におけるクエリはローカルで実行されるので、DCOM およびリモート トラブルシューティングの内容は適用されません。  
  
## <a name="failed-data-collection"></a>データ収集の失敗  
 場合[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ユーティリティのデータ コレクション イベントが失敗し、次の可能性を検討してください。  
  
-   
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のマネージド インスタンス上の "ユーティリティ情報" コレクション セットのプロパティは一切変更しないでください。また、データ コレクションはユーティリティ エージェント ジョブによって制御されるため、データ コレクションのオン/オフを手動で切り替えることも避けてください。  
  
-   WMI 検証に失敗したか、この機能がサポートされていません。 詳細については、このトピックの前半の「WMI 検証の失敗」を参照してください。  
  
-   内のデータとして、マネージ インスタンスのリスト ビュー内のデータを更新[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ユーティリティのビュー ポイントが自動的に更新されません。 データを更新するを右クリックして、**マネージ インスタンス**内のノード、**ユーティリティ エクスプ ローラーのナビゲーション** ウィンドウを選択し、**更新**、または右クリックし、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]リスト ビューで名前をインスタンス化し、選択**更新**です。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスが UCP に登録された後、ユーティリティ エクスプローラーのコンテンツ ウィンドウ内のダッシュボードとビューポイントに最初に表示されるまでに最大 30 分かかる場合があります。  
  
-   インスタンス内のことを確認する SQL Server 構成マネージャーを使用して[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]が実行されています。  
  
-   データ コレクションまたはデータ アップロードがタイムアウトの問題で失敗する場合は、MSDB データベースの dbo.fn_sysutility_mi_get_collect_script() 関数を更新します。 具体的には、"Invoke-BulkCopyCommand()" 関数に次の行を追加します。  
  
    ```  
    $bulkCopy.BulkCopyTimeout=180  
    ```  
  
     タイムアウトの既定値は 30 秒です。  
  
-   ph x="1" /&gt; のインスタンスがクラスター化されていない場合は、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント サービスが実行されていることと、このサービスが UCP、および [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のマネージド インスタンスで自動的に開始するように設定されていることを確認します。  
  
-   マネージ インスタンスでデータ収集を実行する有効なアカウントを使用していることを確認してください。[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]です。 たとえば、パスワードの有効期限が切れている可能性があります。 プロキシ パスワードの有効期限が切れている場合は、次のように、SSMS でパスワード資格情報を更新します。  
  
    1.  SSMS の **オブジェクト エクスプローラー**で、 **[セキュリティ]** ノードを展開し、 **[資格情報]** ノードを展開します。  
  
    2.  右クリックして**utilityagentproxycredential _\<GUID >** 選択**プロパティ**です。  
  
    3.  [資格情報のプロパティ] ダイアログ ボックスで、必要に応じて資格情報の更新、 **utilityagentproxycredential _\<GUID >** 資格情報。  
  
    4.  **[OK]** をクリックして変更を確認します。  
  
-   マネージ インスタンスと UCP で TCP/IP を有効にする必要があります[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]です。 TCP/IP を有効にする[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Configuration Manager です。  
  
-   UCP の SQL Server Browser サービスを開始して、自動的に開始するように構成する必要があります。 組織の方針で SQL Server Browser サービスを使用できない場合は、次の手順を実行して、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のマネージド インスタンスから UCP に接続できるようにします。  
  
    1.  マネージ インスタンスで、Windows タスク バーに[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]、 をクリックして**開始**をクリックし、**を実行しています**.  
  
    2.  該当するボックスに「cliconfg.exe」と入力し、 **[OK]** をクリックします。  
  
    3.  "SQL クライアント設定ユーティリティ EXE" の起動を許可するように求めるメッセージが表示されたら、**[続行]** をクリックします。  
  
    4.  **[SQL クライアント設定ユーティリティ]** ダイアログ ボックスで、 **[別名]** タブをクリックし、 **[追加]** をクリックします。  
  
    5.  **[ネットワーク ライブラリ設定の追加]** ダイアログ ボックスで、次の操作を行います。  
  
    6.  ネットワーク ライブラリの一覧で、[TCP/IP] を指定します。  
  
    7.  **[サーバー別名]** ボックスに、UCP の ComputerName\InstanceName を指定します。  
  
    8.  **[サーバー名]** ボックスに、UCP の ComputerName を指定します。  
  
    9. **[ポートを動的に決定する]** チェック ボックスをオフにします。  
  
    10. **[ポート番号]** ボックスに、UCP がリッスンしているポート番号を指定します。  
  
    11. **[OK]** をクリックして変更を保存します。  
  
    12. マネージ インスタンスごとに次の手順を繰り返して[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]SQL Server Browser サービスが無効になっている UCP に接続します。  
  
-   確認のインスタンスを管理する[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ネットワークに接続します。  
  
-   ph x="1" /&gt; のマネージド インスタンス上に、名前が同じでも大文字と小文字の区別に関する設定が異なるデータベースがある場合は、データベースとそのビューポイントが正しく識別されず、データ収集に失敗することがあります。 たとえば、"MYDATABASE" という名前のデータベースで、実際には "MyDatabase" という名前のデータベースの正常性状態が示される場合があります。 この場合、エラーにはなりません。 データ収集の失敗は、データベース ファイルやファイル グループの名前など、UCP に表示される他のオブジェクトの大文字と小文字の不一致から発生することもあります。  
  
-   ph x="1" /&gt; のマネージド インスタンスが Windows Server 2003 コンピューター上でホストされている場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント サービス アカウントは、Performance Monitor Users セキュリティ グループまたはローカルの Administrators グループに属している必要があります。 属していない場合は、アクセス拒否エラーが発生してデータ収集が失敗します。 追加する、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]エージェント サービス アカウントを Performance Monitor Users セキュリティ グループには、次の手順を使用します。  
  
    1.  **[コンピューターの管理]** を開き、 **[ローカル ユーザーとグループ]**、 **[グループ]** の順に展開します。  
  
    2.  **[Performance Monitor Users]** を右クリックし、 **[グループに追加]** をクリックします。  
  
    3.  **[追加]** をクリックします。  
  
    4.  SQL Server エージェント サービスを実行しているアカウントを入力し、 **[OK]** をクリックします。  
  
    5.  ユーザーをこのグループに追加する前に [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスが既に UCP に登録されている場合は、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント サービスを再起動します。  
  
## <a name="see-also"></a>参照  
 [SQL Server ユーティリティの機能とタスク](../relational-databases/manage/sql-server-utility-features-and-tasks.md)   
 [SQL Server のリソース正常性のトラブルシューティング &#40;SQL Server ユーティリティ&#41;](../relational-databases/manage/troubleshoot-sql-server-resource-health-sql-server-utility.md)  
  
  