---
title: "SQL Server エージェント サービスのアカウントの選択 | Microsoft Docs"
ms.custom: 
ms.date: 05/04/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- roles [SQL Server], SQL Server Agent
- SQL Server Agent, accounts
- startup accounts [SQL Server]
- SQL Server Agent service, accounts
- accounts [SQL Server], SQL Server Agent
- Windows groups [SQL Server Agent]
- SQL Server Agent, permissions
- members [SQL Server], SQL Server Agent service
- Windows domain accounts [SQL Server]
- security [SQL Server], SQL Server Agent
ms.assetid: fe658e32-9e6b-4147-a189-7adc3bd28fe7
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 43841807dce9cb747c2c5b182174f83f0540b030
ms.openlocfilehash: 3050dc3fc207f2154a70c68770ca266d2d47ce92
ms.contentlocale: ja-jp
ms.lasthandoff: 06/23/2017

---
<a id="select-an-account-for-the-sql-server-agent-service" class="xliff"></a>

# SQL Server エージェント サービスのアカウントの選択
サービス開始アカウントにより、 [!INCLUDE[msCoName](../../includes/msconame_md.md)] エージェントを実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Windows アカウントとそのネットワーク権限が定義されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントは、指定されたユーザー アカウントで実行されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 構成マネージャーを使用して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスのアカウントを選択します。構成マネージャーでは、次のオプションから選択できます。  
  
-   **[ビルトイン アカウント]**。 次のビルトイン Windows サービス アカウントの一覧から選択できます。  
  
    -   **[ローカル システム]** アカウント。 このアカウントの名前は NT AUTHORITY\System です。 これは、すべてのローカル システム リソースに無制限にアクセスできる強力なアカウントです。 これは、ローカル コンピューターの Windows **Administrators** グループのメンバーです。つまり [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **sysadmin** 固定サーバー ロールのメンバーです。  
  
        > [!IMPORTANT]  
        > **[ローカル システム アカウント]** オプションは、旧バージョンとの互換性のためだけに用意されています。 ローカル システム アカウントには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントが必要としない権限があります。 ローカル システム アカウントとして [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントを実行するのは避けてください。 セキュリティを強化するには、次の「Windows ドメイン アカウントの権限」に示す権限のある Windows ドメイン アカウントを使用します。  
  
-   **[このアカウント]**。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスを実行する Windows ドメイン アカウントを指定します。 Windows **Administrators** グループのメンバーではない Windows ユーザー アカウントを選択することをお勧めします。 ただし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービス アカウントがローカル **Administrators** グループのメンバーではない場合、マルチサーバー管理の使用には制限があります。 詳細については、後の「サポートされるサービス アカウントの種類」を参照してください。  
  
<a id="windows-domain-account-permissions" class="xliff"></a>

## Windows ドメイン アカウントの権限  
セキュリティを強化するには、 **[このアカウント]**を選択して、Windows ドメイン アカウントを指定します。 指定する Windows ドメイン アカウントは、次の権限を所持している必要があります。  
  
-   すべてのバージョンの Windows で、サービスとしてログオンする権限 (SeServiceLogonRight)。  
  
> [!NOTE]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービス アカウントは、ドメイン コントローラーの Pre-Windows 2000 Compatible Access グループに所属している必要があります。このグループに所属していないと、Windows Administrators グループのメンバー以外のドメイン ユーザーが所有するジョブが失敗します。  
  
-   Windows サーバーでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント プロキシをサポートできるように、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスを実行しているアカウントに次の権限が必要になります。  
  
    -   スキャン チェックをバイパスする権限 (SeChangeNotifyPrivilege)  
  
    -   プロセス レベル トークンを置き換える権限 (SeAssignPrimaryTokenPrivilege)  
  
    -   プロセスに対してメモリ クォータを調整する権限 (SeIncreaseQuotaPrivilege)  
  
    -   ネットワーク (SeNetworkLogonRight) からこのコンピューターにアクセスする権限  
  
> [!NOTE]  
> アカウントにプロキシのサポートに必要な権限がない場合は、 **sysadmin** 固定サーバー ロールのメンバーのみがジョブを作成できます。  
  
> [!NOTE]  
> WMI 警告の通知を受信するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントのサービス アカウントに、WMI イベントを含む名前空間、および ALTER ANY EVENT NOTIFICATION に対する権限が許可されている必要があります。  
  
<a id="sql-server-role-membership" class="xliff"></a>

## SQL Server ロールのメンバーシップ  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスを実行するアカウントは、次の [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ロールのメンバーである必要があります。  
  
-   アカウントは、 **sysadmin** 固定サーバー ロールのメンバーでなければなりません。  
  
-   マルチサーバー ジョブの処理を使用するには、アカウントはマスター サーバーの **msdb** データベースの **TargetServersRole** ロールのメンバーでなければなりません。  
  
<a id="supported-service-account-types" class="xliff"></a>

## サポートされるサービス アカウントの種類  
以下の表に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスで使用できる Windows アカウントの種類を示します。  
  
|サービス アカウントの種類|非クラスター化サーバー|クラスター化サーバー|ドメイン コントローラー (非クラスター化)|  
|------------------------|-------------------------|--------------------|--------------------------------------|  
|[!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows ドメイン アカウント (Windows Administrators グループのメンバー)|Supported|Supported|Supported|  
|Windows ドメイン アカウント (管理者以外)|Supported<br /><br />以下に示す制限事項 1 を参照してください。|Supported<br /><br />以下に示す制限事項 1 を参照してください。|Supported<br /><br />以下に示す制限事項 1 を参照してください。|  
|ネットワーク サービス アカウント (NT AUTHORITY\NetworkService)|Supported<br /><br />以下に示す制限事項 1、3、4 を参照してください。|サポートされていません|サポートされていません|  
|ローカル ユーザー アカウント (管理者以外)|Supported<br /><br />以下に示す制限事項 1 を参照してください。|サポートされていません|適用なし|  
|ローカル システム アカウント (NT AUTHORITY\System)|Supported<br /><br />以下に示す制限事項 2 を参照してください。|サポートされていません|Supported<br /><br />以下に示す制限事項 2 を参照してください。|  
|ローカル サービス アカウント (NT AUTHORITY\LocalService)|サポートされていません|サポートされていません|サポートされていません|  
  
<a id="limitation-1-using-non-administrative-accounts-for-multiserver-administration" class="xliff"></a>

### 制限事項 1 : マルチサーバー管理での非管理者アカウントの使用  
対象サーバーをマスター サーバーに参加させると、"参加操作に失敗しました" というエラー メッセージが表示されることがあります。  
  
このエラーを解決するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] と [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスの両方を再起動します。 詳細については、「 [Start, Stop, Pause, Resume, Restart the Database Engine, SQL Server Agent, or SQL Server Browser Service](http://msdn.microsoft.com/en-us/32660a02-e5a1-411a-9e57-7066ca459df6)」を参照してください。  
  
<a id="limitation-2-using-the-local-system-account-for-multiserver-administration" class="xliff"></a>

### 制限事項 2 : マルチサーバー管理でのローカル システム アカウントの使用  
マルチサーバー管理は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスがローカル システム アカウントで実行されるとき、同じコンピューターにマスター サーバーと対象サーバーの両方が存在する場合にのみサポートされます。 この構成を使用している場合に、対象サーバーをマスター サーバーに参加させると、次のメッセージが返されます。  
  
"*<target_server_computer_name>* のエージェント開始アカウントに対象サーバーとしてのログオン権限があることを確認します"  
  
情報提供を目的としたこのメッセージは無視できます。 参加操作は、正常に完了します。 詳細については、「 [マルチサーバー環境の作成](../../ssms/agent/create-a-multiserver-environment.md)」を参照してください。  
  
<a id="limitation-3-using-the-network-service-account-when-it-is-a-sql-server-user" class="xliff"></a>

### 制限事項 3 : SQL Server ユーザーであるネットワーク サービス アカウントの使用  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスをネットワーク サービス アカウントで実行する場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] インスタンスに [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ユーザーとしてログインするアクセス権がそのネットワーク サービス アカウントに明示的に与えられていると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントが起動しないことがあります。  
  
これを解決するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] が実行されているコンピューターを再起動します。 これは一度実行するだけで済みます。  
  
<a id="limitation-4-using-the-network-service-account-when-sql-server-reporting-services-is-running-on-the-same-computer" class="xliff"></a>

### 制限事項 4 : SQL Server Reporting Services が同じコンピューターで実行されている場合のネットワーク サービス アカウントの使用  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスをネットワーク サービス アカウントで実行する場合、同じコンピューターで [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] も動作していると、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion_md.md)] エージェントが起動しないことがあります。  
  
これを解決するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] が実行されているコンピューターを再起動し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] と [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービスの両方を再起動します。 これは一度実行するだけで済みます。  
  
<a id="common-tasks" class="xliff"></a>

## 一般的なタスク  
**SQL Server エージェント サービスの開始アカウントを指定するには**  
  
-   [Set the Service Startup Account for SQL Server Agent (SQL Server Configuration Manager)](../../ssms/agent/set-service-startup-account-sql-server-agent-sql-server-configuration-manager.md)  
  
**SQL Server エージェントのメール プロファイルを指定するには**  
  
-   [データベース メールを使用するように SQL Server エージェント メールを構成する方法 (SQL Server Management Studio)](http://msdn.microsoft.com/en-us/4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce)  
  
> [!NOTE]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 構成マネージャーを使用して、オペレーティング システムを起動するときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントを開始する必要があることを指定します。  
  
<a id="see-also" class="xliff"></a>

## 参照  
[Windows サービス アカウントの設定](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014)  
[サービスの管理方法に関するトピック (SQL Server 構成マネージャー)](http://msdn.microsoft.com/en-us/78dee169-df0c-4c95-9af7-bf033bc9fdc6)  
[SQL Server エージェントのセキュリティの実装](../../ssms/agent/implement-sql-server-agent-security.md)  
  

