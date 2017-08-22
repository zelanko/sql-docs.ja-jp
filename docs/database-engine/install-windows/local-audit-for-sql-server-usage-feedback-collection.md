---
title: "SQL Server Usage Feedback Collection の Local Audit | Microsoft Docs"
ms.custom: 
ms.date: 02/28/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- dbe-security
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Local Audit
ms.assetid: a0665916-7789-4f94-9086-879275802cf3
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 01f20dd99963b0bb1be86ddc3e173aef6fb3e8b3
ms.openlocfilehash: a768e5237b997e5f9b05e9476c907ea66f886c7b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/11/2017

---
# <a name="local-audit-for-sql-server-usage-feedback-collection"></a>SQL Server Usage Feedback Collection の Local Audit
## <a name="introduction"></a>概要

Microsoft SQL Server は、お客様のコンピューターまたはデバイスに関する情報 (以下「標準的なコンピューター情報」といいます) を収集してマイクロソフトに送信するインターネット対応の機能を備えています。 [SQL Server Usage Feedback Collection](http://support.microsoft.com/kb/3153756) の Local Audit コンポーネントは、サービスで収集されたデータを保存先フォルダーに出力します。このデータは、Microsoft に送信されるデータ (ログ) です。 Local Audit の目的は、Microsoft がこの機能で収集するすべてのデータをユーザーがコンプライアンス、法規制、またはプライバシーの検証目的で確認できるようにすることです。  

SQL Server 2016 CU2 以降、Local Audit は SQL Server Database Engine and Analysis Services (SSAS) のインスタンス レベルで構成できるようになりました。 SQL Server 2016 CU4 および SQL Server 2016 SP1 では、Local Audit は SQL Server Integration Services (SSIS) に対しても有効になります。 セットアップ中にインストールされる他の SQL Server コンポーネントと、セットアップ後にダウンロードまたはインストールされる SQL Server ツールには、使用状況フィードバック収集用の Local Audit 機能はありません。 

## <a name="prerequisites"></a>前提条件 

各 SQL Server インスタンスで Local Audit を有効にする前提条件は次のとおりです。 

1. インスタンスには SQL Server 2016 RTM CU2 以降の修正プログラムが適用されている。 

1. ユーザーはシステム管理者であるか、レジストリ キーの追加および変更、フォルダーの作成、フォルダー セキュリティの管理、および Windows サービスの停止/開始を行うアクセス権を持つロールである必要があります。  

## <a name="pre-configuration-steps-prior-to-turning-on-local-audit"></a>Local Audit を有効にする前の事前構成手順 

Local Audit を有効にする前に、システム管理者には次の準備が必要です。

1. SQL Server インスタンス名と SQL Server CEIP テレメトリ サービス ログオン アカウントを把握する。 

1. Local Audit ファイル用の新しいフォルダーを構成する。

1. SQL Server CIEP テレメトリ サービス ログオン アカウントにアクセス許可を付与する。

1. Local Audit ターゲット ディレクトリを構成するレジストリ キー設定を作成する。 

    データベース エンジンと Integration Services の場合、*HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSSQL14.\<INSTANCENAME\>\\CPE* にキーを作成します。 
    
    Analysis Services の場合、*HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSAS14.\<INSTANCENAME\>\\CPE* にキーを作成します。

### <a name="get-the-sql-server-ceip-service-logon-account"></a>SQL Server CEIP サービス ログイン アカウントを取得する

次の手順で、SQL Server CEIP テレメトリ サービス ログイン アカウントを取得します
 
1. **[サービス]** を起動します ( **[Windows]**  ボタンをクリックし、「 *services.msc*」と入力します) 

2. 目的のサービスに移動します。 たとえば、データベース エンジンの場合、 **SQL Server CEIP service \<インスタンス名\>**にキーを作成します。 Analysis Services の場合、**SQL Server Analysis Services CEIP \<インスタンス名\>** を探します。 Integration Services の場合は、**SQL Server Integration Services CEIP サービス 13** を探します。

3. サービスを右クリックし、 **[プロパティ]**を選択します。 

4. **[ログオン]** タブをクリックします。 ログオン アカウントは **[このアカウント]**に表示されます。 

### <a name="configure-a-new-folder-for-the-local-audit-files"></a>Local Audit ファイル用の新しいフォルダーを構成する。    

Local Audit がログを出力する新しいフォルダー (Local Audit ディレクトリ) を作成します。 たとえば、データベース エンジンの既定インスタンスの Local Audit ディレクトリの完全なパスは、*C:\\SQLCEIPAudit\\MSSQLSERVER\\DB\\* です。 
 
> 注: 監査機能や修正プログラムによって SQL Server に問題が発生する可能性を防ぐには、SQL Server インストール パス以外の Local Audit のディレクトリ パスを構成してください。

  ||設計上の決定|推奨|  
  |------|-----------------|----------|  
  |![チェック ボックス](../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|空き領域 |データベース数が約 10 個で中程度のワークロードの場合、インスタンスごとに 1 日約 2 MB のディスク領域で計画を立てます。|  
|![チェック ボックス](../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|別のディレクトリ | 各インスタンス用にディレクトリを作成します。 たとえば、`MSSQLSERVER` という SQL Server インスタンス用には *C:\\SQLCEIPAudit\\MSSQLSERVER\\DB\\* を使用します。 こうすることでファイルの管理が簡単になります。
|![チェック ボックス](../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|別のディレクトリ |サービスごとに別のフォルダーを使用します。 たとえば、1 つのインスタンス名について、データベース エンジン用に 1 つのフォルダーを用意します。 SSAS のインスタンスで同じインスタンス名を使用する場合は、SSAS 用に別のフォルダーを作成します。 データベース エンジンと Analysis Services の両インスタンスを同じフォルダーに構成すると、すべての Local Audit で両インスタンスのログが同じログ ファイルに出力されます。| 
|![チェック ボックス](../../database-engine/availability-groups/windows/media/checkboxemptycenterxtraspacetopandright.gif "チェック ボックス")|SQL Server CIEP テレメトリ サービス ログオン アカウントにアクセス許可を付与する|SQL Server CEIP テレメトリ サービス ログイン アカウントに対する **フォルダーの内容の一覧表示**、 **読み取り** 、および **書き込み** の各アクセス権を有効にします|


### <a name="grant-permissions-to-the-sql-server-ciep-telemetry-service-logon-account"></a>SQL Server CIEP テレメトリ サービス ログオン アカウントにアクセス許可を付与する
  
1. **エクスプローラー**で、新しいフォルダーがある場所に移動します。  

1. 新しいフォルダーを右クリックし、 **[プロパティ]**をクリックします。 

1. **[セキュリティ]**タブの **[編集]** をクリックし、権限を管理します。

1. **[追加]** をクリックし、SQL Server CEIP テレメトリ サービスの資格情報を入力します (例: `NT Service\SQLTELEMETRY`)。   

1. **[名前の確認]** をクリックして入力した名前を検証し、 **[OK]**をクリックします。 

1. **[権限]** ダイアログ ボックスで、SQL Server CEIP テレメトリ サービスのログオン アカウントを選択し、 **[フォルダーの内容の一覧表示]**、 **[読み取り]** 、 **[書き込み]**をクリックします。  

1. **[OK]** をクリックすると、権限の変更が直ちに適用されます。 
  
### <a name="create-a-registry-key-setting-to-configure-local-audit-target-directory"></a>Local Audit ターゲット ディレクトリを構成するレジストリ キー設定を作成する。

1. regedit を起動します。  

1. 目的の CPE パスに移動します。 

    データベース エンジンと Integration Services の場合、*HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSSQL14.\<INSTANCENAME\>\\CPE* を使用します。 
    
    Analysis Services の場合、*HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSAS14.\<INSTANCENAME\>\\CPE* を使用します。

1. CPE パスを右クリックし、 **[新規]**を選択します。 **[文字列値]**をクリックします。

1. 新しいレジストリ キーに `UserRequestedLocalAuditDirectory`と名前を付けます。 
 
## <a name="turning-local-audit-on-or-off"></a>Local Audit の有効/無効を切り替える

事前構成手順を完了したら、Local Audit を有効にすることができます。 有効にするには、システム管理者アカウント、またはレジストリ キーを変更するアクセス権を持つ同様のロールを使用し、次の手順に従って Local Audit の有効/無効を切り替えます。 

1. **regedit**を起動します。  

1. 目的の CPE パスに移動します。 

    データベース エンジンと Integration Services の場合、*HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSSQL14.\<INSTANCENAME\>\\CPE* を使用します。 
    
    Analysis Services の場合、*HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Microsoft SQL Server\\MSAS14.\<INSTANCENAME\>\\CPE* を使用します。

1. **[UserRequestedLocalAuditDirectory]** を右クリックし、 *[変更]*をクリックします。 

1. Local Audit を有効にするには、Local Audit のパスを入力します (例: *C:\\SQLCEIPAudit\\MSSQLSERVER\\DB\\*)。
 
    Local Audit を無効にするには、**[UserRequestedLocalAuditDirectory]** の値を空にします。

1. **regedit**を閉じます。 

SQL Server CEIP が既に実行中の場合、Local Audit 設定は直ちに認識されます。 SQL Server CEIP サービスを開始するには、システム管理者、または Windows サービスを開始または停止するアクセス権を持つユーザーが、次の手順を実行します。 

1. Windows ボタンをクリックし、「Services」と入力して、サービス アプリケーションを起動します。 

1. 目的のサービスに移動します。 

    データベース エンジンの場合、「**SQL Server CEIP service (\<インスタンス名\>)**」を使用します。 
    
    Analysis Services の場合、「**SQL Server Analysis Services CEIP (\<インスタンス名\>)**」を使用します。 

1. サービスを右クリックし、[再起動] を選択します。 

1. サービスの状態が " **実行中**" であることを確認します。 

Local Audit では、1 日に 1 つのログ ファイルが生成されます。 ログ ファイルは `<YYYY-MM-DD>.json`の形式です。 たとえば、 *2016-07-12.json*というファイル名です。 保存先ディレクトリにその日のファイルが既にある場合、Local Audit のログはそのファイルに付加されます。 既存のファイルがない場合、その日の新しいファイルが作成されます。 

> 注: Local Audit を有効にしてから、初めてログ ファイルに出力されるまでに最長 5 分間かかることがあります。 

## <a name="maintenance"></a>メンテナンス 

1. Local Audit から出力されるファイルのディスク使用量を制限するには、Local Audit ディレクトリをクリーンアップして古い不要なファイルを削除するポリシーまたは定期ジョブを設定します。  

2. Local Audit ディレクトリ パスには適切なユーザーのみがアクセスできるようにセキュリティで保護します。 ログ ファイルには、「 [How to configure SQL Server 2016 to send feedback to Microsoft](http://support.microsoft.com/kb/3153756)」(フィードバックを Microsoft に送信するように SQL Server 2016 を構成する方法) で説明されている情報が含まれています。 このファイルに対するアクセス権では、組織のほとんどのメンバーに読み取りを禁止することが推奨されます。  

## <a name="data-dictionary-of-local-audit-output-data-structure"></a>Local Audit 出力データ構造のデータ辞書 

- Local Audit ログ ファイルは JSON 形式です。 **emitTime**で Microsoft に送信されるデータ ポイントを表すオブジェクト (行) のセットが含まれます。  

- 各行は、 **schemaVersion**に指定された特定のスキーマに従います。   

- 各行は、 **sessionID**に指定された SQLCEIP サービス セッションの出力です。  

- 行は、 **sequence**に指定された順に出力されます。 

- 各データ ポイント行には、 **queryIdentifier** の出力が含まれています。この出力は、 **traceName**に指定されたトレースの種類に関連する T-SQL クエリ、XE セッション、またはメッセージの可能性があります。   

- **queryIdentifiers** はグループ化され、 **querySetVersion**を使用してバージョン管理されます。 

- **data** には、 **queryTimeInTicks**を使用した対応するクエリ実行の出力が含まれます。 

- T-SQL クエリの**queryIdentifiers** によって、クエリに T-SQL クエリ定義が格納されます。 


| 論理的な Local Audit 情報階層 | 関連する列 |
| ------ | -------|
| Header | emitTime、schemaVersion 
| Machine | hostname、domainHash、sqmID、operatingSystem 
| Instance | instanceName、correlationID、clientVersion 
| Session | sessionID、traceName 
| Query | sequence、querySetVersion、queryIdentifier、query、queryTimeInTicks 
| data |  data 

### <a name="namevalue-pairs-definition-and-examples"></a>名前/値ペアの定義と例 

以下の列は、Local Audit ファイル出力の順を表しています。 以下の複数列の匿名化された値に対して、SHA 256 による一方向のハッシュが使用されています。  

| 名前 | 説明 | 値の例
|-------|--------| ----------|
|hostname | SQL Server がインストールされている匿名化されたコンピューター名| de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11 
|domainHash| SQL Server インスタンスをホストするコンピューターの匿名化されたドメイン ハッシュ | de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11 
|sqmId |SQL Server がインストールされているコンピューターを表す識別子 | 02AF58F5-753A-429C-96CD-3900E90DB990 
|INSTANCENAME| 匿名化された SQL Server インスタンス名| e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855 
|schemaVersion| SQLCEIP のスキーマ バージョン |  3 
|emitTime |データ ポイントの生成時間 (UTC) | 2016-09-08T17:20:22.1124269Z 
|sessionID | SQLCEIP サービスを提供するセッション識別子 | 89decf9a-ad11-485c-94a7-fefb3a02ed86 
| correlationId | 追加の識別子のプレース ホルダー | 0 
|sequence | セッション内で送信されたデータ ポイントのシーケンス番号 | 15 
| clientVersion | SQL Server インスタンスのバージョン | 13.0.2161.3 ((SQL16_RTM_QFE-CU).160907-1223) 
| operatingSystem | SQL Server インスタンスがインストールされている OS バージョン | Microsoft Windows Server 2012 R2 Datacenter 
| querySetVersion | クエリ定義グループのバージョン | 1.0.0.0 
|traceName | トレースのカテゴリ: (SQLServerXeQueries、SQLServerPeriodicQueries、SQLServerOneSettingsException) | SQLServerPeriodicQueries 
|queryIdentifier | クエリの識別子 | SQLServerProperties.002 
|data   | T-SQL クエリ、XE セッション、またはアプリケーションの出力として queryIdentifier で収集された情報の出力 |   [{"Collation": "SQL_Latin1_General_CP1_CI_AS","SqlFTinstalled": "0" "SqlIntSec": "1","IsSingleUser": "0","SqlFilestreamMode": "0","SqlPbInstalled": "0","SqlPbNodeRole": "","SqlVersionMajor": "13","SqlVersionMinor": "0","SqlVersionBuild": "2161","ProductBuildType": "","ProductLevel": "RTM","ProductUpdateLevel": "CU2","ProductUpdateReference": "KB3182270","ProductRevision": "3","SQLEditionId": "-1534726760","IsClustered": "0","IsHadrEnabled": "0","SqlAdvAInstalled": "0","PacketReceived": "1210","Version": "Microsoft SQL Server 2016 (RTM-CU2) (KB3182270) - 13.0.2161.3 (X64) \n\tSep  7 2016 14:24:16 \n\tCopyright (c) Microsoft Corporation\n\tStandard Edition (64-bit) on Windows Server 2012 R2 Datacenter 6.3 \u003cX64\u003e (Build 9600: ) (Hypervisor)\n"}],
|Query| 該当する場合、データを生成した queryIdentifier に関連する T-SQL クエリ定義。        このコンポーネントは、SQL Server CEIP サービスでアップロードされません。 ユーザー専用の参照コンポーネントとして Local Audit に含まれています。| SELECT\n      SERVERPROPERTY(\u0027Collation\u0027) AS [Collation],\n      SERVERPROPERTY(\u0027IsFullTextInstalled\u0027) AS [SqlFTinstalled],\n      SERVERPROPERTY(\u0027IsIntegratedSecurityOnly\u0027) AS [SqlIntSec],\n      SERVERPROPERTY(\u0027IsSingleUser\u0027) AS [IsSingleUser],\n      SERVERPROPERTY (\u0027FileStreamEffectiveLevel\u0027) AS [SqlFilestreamMode],\n      SERVERPROPERTY(\u0027IsPolybaseInstalled\u0027) AS [SqlPbInstalled],\n      SERVERPROPERTY(\u0027PolybaseRole\u0027) AS [SqlPbNodeRole],\n      SERVERPROPERTY(\u0027ProductMajorVersion\u0027) AS [SqlVersionMajor],\n      SERVERPROPERTY(\u0027ProductMinorVersion\u0027) AS [SqlVersionMinor],\n      SERVERPROPERTY(\u0027ProductBuild\u0027) AS [SqlVersionBuild],\n      SERVERPROPERTY(\u0027ProductBuildType\u0027) AS ProductBuildType,\n      SERVERPROPERTY(\u0027ProductLevel\u0027) AS ProductLevel,\n      SERVERPROPERTY(\u0027ProductUpdateLevel\u0027) AS ProductUpdateLevel,\n      SERVERPROPERTY(\u0027ProductUpdateReference\u0027) AS ProductUpdateReference,\n      RIGHT(CAST(SERVERPROPERTY(\u0027ProductVersion\u0027) AS NVARCHAR(30)),CHARINDEX(\u0027.\u0027, REVERSE(CAST(SERVERPROPERTY(\u0027ProductVersion\u0027) AS NVARCHAR(30)))) - 1) AS ProductRevision,\n      SERVERPROPERTY(\u0027EditionID\u0027) AS SQLEditionId,\n      SERVERPROPERTY(\u0027IsClustered\u0027) AS IsClustered,\n      SERVERPROPERTY(\u0027IsHadrEnabled\u0027) AS IsHadrEnabled,\n      SERVERPROPERTY(\u0027IsAdvancedAnalyticsInstalled\u0027) AS [SqlAdvAInstalled],\n      @@PACK_RECEIVED AS PacketReceived,\n      @@VERSION AS Version
|queryTimeInTicks | 次のトレース カテゴリのクエリを実行するためにかかる期間: (SQLServerXeQueries、SQLServerPeriodicQueries) |  0 
 
### <a name="trace-categories"></a>トレース カテゴリ 
現在、次のトレース カテゴリを収集します。 

- **SQLServerXeQueries**: 拡張イベント セッションで収集されたデータ ポイントが含まれます。 

- **SQLServerPeriodicQueries**: SQL Server インスタンスで実行される定期的なクエリで収集されたデータ ポイントが含まれます。 

- **SQLServerPerDBPeriodicQueries**: SQL Server インスタンスの最大 30 データベースに対して実行される定期的なクエリで収集されたデータ ポイントが含まれます。 

- **SQLServerOneSettingsException**: スキーマやクエリ セットの更新に関連する例外メッセージが含まれます。 

- **DigitalProductID**: SQL Server インスタンスの匿名化された (SHA-256) ハッシュ デジタル プロダクト ID を集約するデータ ポイントが含まれます。 

### <a name="local-audit-file-examples"></a>Local Audit ファイルの例



次に Local Audit の JSON ファイル出力の例を示します。

```JSON
{
    "hostName": "de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11",
    "domainHash": "de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11",
    "sqmId": "02AF58F5-753A-429C-96CD-3900E90DB990",
    "instanceName": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
    "schemaVersion": "3",
    "emitTime": "2016-09-08T17:20:22.1124269Z",
    "sessionId": "89decf9a-ad11-485c-94a7-fefb3a02ed86",
    "correlationId": 0,
    "sequence": 15,
    "clientVersion": "13.0.2161.3 ((SQL16_RTM_QFE-CU).160907-1223)",
    "operatingSystem": "Microsoft Windows Server 2012 R2 Datacenter",
    "querySetVersion": "1.0.0.0",
    "traceName": "SQLServerPeriodicQueries",
    "queryIdentifier": "SQLServerProperties.002",
    "data": [
      {
        "Collation": "SQL_Latin1_General_CP1_CI_AS",
        "SqlFTinstalled": "0",
        "SqlIntSec": "1",
        "IsSingleUser": "0",
        "SqlFilestreamMode": "0",
        "SqlPbInstalled": "0",
        "SqlPbNodeRole": "",
        "SqlVersionMajor": "13",
        "SqlVersionMinor": "0",
        "SqlVersionBuild": "2161",
        "ProductBuildType": "",
        "ProductLevel": "RTM",
        "ProductUpdateLevel": "CU2",
        "ProductUpdateReference": "KB3182270",
        "ProductRevision": "3",
        "SQLEditionId": "-1534726760",
        "IsClustered": "0",
        "IsHadrEnabled": "0",
        "SqlAdvAInstalled": "0",
        "PacketReceived": "1210",
        "Version": "Microsoft SQL Server 2016 (RTM-CU2) (KB3182270) - 13.0.2161.3 (X64) \n\tSep  7 2016 14:24:16 \n\tCopyright (c) Microsoft Corporation\n\tStandard Edition (64-bit) on Windows Server 2012 R2 Datacenter 6.3 \u003cX64\u003e (Build 9600: ) (Hypervisor)\n"
      }
    ],
    "query": "SELECT\n      SERVERPROPERTY(\u0027Collation\u0027) AS [Collation],\n      SERVERPROPERTY(\u0027IsFullTextInstalled\u0027) AS [SqlFTinstalled],\n      SERVERPROPERTY(\u0027IsIntegratedSecurityOnly\u0027) AS [SqlIntSec],\n      SERVERPROPERTY(\u0027IsSingleUser\u0027) AS [IsSingleUser],\n      SERVERPROPERTY (\u0027FileStreamEffectiveLevel\u0027) AS [SqlFilestreamMode],\n      SERVERPROPERTY(\u0027IsPolybaseInstalled\u0027) AS [SqlPbInstalled],\n      SERVERPROPERTY(\u0027PolybaseRole\u0027) AS [SqlPbNodeRole],\n      SERVERPROPERTY(\u0027ProductMajorVersion\u0027) AS [SqlVersionMajor],\n      SERVERPROPERTY(\u0027ProductMinorVersion\u0027) AS [SqlVersionMinor],\n      SERVERPROPERTY(\u0027ProductBuild\u0027) AS [SqlVersionBuild],\n      SERVERPROPERTY(\u0027ProductBuildType\u0027) AS ProductBuildType,\n      SERVERPROPERTY(\u0027ProductLevel\u0027) AS ProductLevel,\n      SERVERPROPERTY(\u0027ProductUpdateLevel\u0027) AS ProductUpdateLevel,\n      SERVERPROPERTY(\u0027ProductUpdateReference\u0027) AS ProductUpdateReference,\n      RIGHT(CAST(SERVERPROPERTY(\u0027ProductVersion\u0027) AS NVARCHAR(30)),CHARINDEX(\u0027.\u0027, REVERSE(CAST(SERVERPROPERTY(\u0027ProductVersion\u0027) AS NVARCHAR(30)))) - 1) AS ProductRevision,\n      SERVERPROPERTY(\u0027EditionID\u0027) AS SQLEditionId,\n      SERVERPROPERTY(\u0027IsClustered\u0027) AS IsClustered,\n      SERVERPROPERTY(\u0027IsHadrEnabled\u0027) AS IsHadrEnabled,\n      SERVERPROPERTY(\u0027IsAdvancedAnalyticsInstalled\u0027) AS [SqlAdvAInstalled],\n      @@PACK_RECEIVED AS PacketReceived,\n      @@VERSION AS Version",
    "queryTimeInTicks": 0
  } ,
  {
    "hostName": "de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11",
    "domainHash": "de3b3769a63970b63981ab7a956401388962c986bfd39d371f5870d800627d11",
    "sqmId": "02AF58F5-753A-429C-96CD-3900E90DB990",
    "instanceName": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
    "schemaVersion": "3",
    "emitTime": "2016-09-08T17:20:24.9819144Z",
    "sessionId": "89decf9a-ad11-485c-94a7-fefb3a02ed86",
    "correlationId": 0,
    "sequence": 61,
    "clientVersion": "13.0.2161.3 ((SQL16_RTM_QFE-CU).160907-1223)",
    "operatingSystem": "Microsoft Windows Server 2012 R2 Datacenter",
    "querySetVersion": "1.0.0.0",
    "traceName": "SQLServerPeriodicQueries",
    "queryIdentifier": "ExternalScriptStats.001",
    "data": [
      {
        "counter_name": "Total Executions                                                                                                                ",
        "cntr_value": "0"
      },
      {
        "counter_name": "Parallel Executions                                                                                                             ",
        "cntr_value": "0"
      },
      {
        "counter_name": "Streaming Executions                                                                                                            ",
        "cntr_value": "0"
      },
      {
        "counter_name": "SQL CC Executions                                                                                                               ",
        "cntr_value": "0"
      },
      {
        "counter_name": "Implied Auth. Logins                                                                                                            ",
        "cntr_value": "0"
      },
      {
        "counter_name": "Total Execution Time (ms)                                                                                                       ",
        "cntr_value": "0"
      },
      {
        "counter_name": "Execution Errors                                                                                                                ",
        "cntr_value": "0"
      }
    ],  
    "query": "select counter_name, cntr_value from sys.dm_os_performance_counters where object_name like \u0027%External Scripts%\u0027",
    "queryTimeInTicks": 155834
  } 
```
## <a name="frequently-asked-questions"></a>よく寄せられる質問

**DBA で Local Audit ログ ファイルを読み取るにはどうすればよいですか?**
Local Audit ログ ファイルは JSON 形式で出力されます。 各行は、Microsoft にアップロードされた 1 件のテレメトリを表す JSON オブジェクトになります。 フィールドには、わかりやすい名前を付けることをお勧めします。 

**DBA で Usage Feedback Collection を無効にするとどうなりますか?**
Local Audit ファイルが出力されなくなります。 

**インターネット接続がない場合やコンピューターがファイアウォールの背後にある場合はどうなりますか?**
SQL Server 2016 の使用状況のフィードバックは Microsoft に送信されなくなります。 構成が正しければ、Local Audit ログの出力は試行されます。

**DBA で Local Audit を無効にするにはどうすればよいですか?**
UserRequestedLocalAuditDirectory レジストリ キー エントリを削除します。

**Local Audit ログ ファイルを読み取ることができるのは誰ですか?**
組織内で、Local Audit ディレクトリにアクセス権を持つ全員です。

**指定したディレクトリに出力されたログ ファイルを DBA で管理するにはどうすればよいですか?**
ディスク領域を消費しすぎないように、ディレクトリ内にあるファイルのクリーンアップを DBA で自動管理する必要があります。

**この JSON 出力を読み取るために使用できるクライアントまたはツールはありますか?**
出力は、メモ帳、Visual Studio、JSON リーダーなど任意のツールで読み取ることができます。
また、JSON ファイルを読み取り、以下の図のように SQL Server 2016 インスタンスのデータを分析することもできます。 SQL Server で JSON ファイルを読み取る方法の詳細については、「 [Importing JSON files into SQL Server using OPENROWSET (BULK) and OPENJSON (Transact-SQL)](http://blogs.msdn.microsoft.com/sqlserverstorageengine/2015/10/07/bulk-importing-json-files-into-sql-server/)」(OPENROWSET (BULK) と OPENJSON (Transact-SQL) を使用して JSON ファイルを SQL Server にインポートする) を参照してください。

```Transact-SQL
DECLARE @JSONFile AS VARCHAR(MAX)

-- Read the JSON file into variable 
SELECT @JSONFile = BulkColumn 
FROM OPENROWSET (BULK 'C:\SQLCEIPAudit\MSSQLSERVER\2016-09-08.json', SINGLE_CLOB) MyFile 

-- Check if the JSON file has been read properly and if it's in a JSON format
SELECT 
    @JSONFile LocalAuditOutput, 
    ISJSON(@JSONFile) IsFileInJSONFormat

-- Get the query identifier, query and the data (output of the query)   
SELECT 
    sequence,
    queryIdentifier,
    query,
    data
FROM OPENJSON(@JSONFile) 
    WITH (sessionId VARCHAR(64)
         ,sequence INT
         ,queryIdentifier VARCHAR(128)
         ,query VARCHAR(MAX)
         ,data NVARCHAR(MAX) AS JSON)
-- Get specific details about the output of "DatabaseProperties.001" query  
SELECT 
    QueryIdentifier,
    DatabaseID,
    CompatibilityLevel,
    IsQueryStoreOn
FROM OPENJSON(@JSONFile) 
    WITH (sessionId VARCHAR(64)
         ,sequence INT
         ,queryIdentifier VARCHAR(128)
         ,query VARCHAR(MAX)
         ,data NVARCHAR(MAX) AS JSON) 
    CROSS APPLY OPENJSON(data) 
        WITH (   DatabaseID varchar(128) '$.database_id'
                ,CompatibilityLevel varchar(128) '$.compatibility_level'
                ,IsQueryStoreOn varchar(128) '$.QS'
             )
WHERE queryIdentifier = 'DatabaseProperties.001'
```

## <a name="see-also"></a>参照
[SSMS Usage Feedback Collection の Local Audit](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-telemetry-ssms)


