---
title: "高度な分析拡張機能の構成および管理 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "11/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8d73fd98-0c61-4a62-94bb-75658195f2a6
caps.latest.revision: 21
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 20
---
# 高度な分析拡張機能の構成および管理
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)]をインストールすると、R のランタイムおよび [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] に関連するその他のサービスの構成に軽微な変更を行うことができます。  
  
  
 **このトピックの内容**  
  
-   [SQL Server R Services のユーザー アカウントをプロビジョニングする](#bkmk_Provisioning)  
  
-   [R プロセスによるメモリの使用を管理する](#bkmk_ManagingMemory)  
  
-   [構成ファイルを使用してサービスの既定値を変更する](#bkmk_ChangingConfig) 

-   [スタート パッド サービス アカウントを変更します。](#bkmk_Launchpad) 
  
##  <a name="bkmk_Provisioning"></a> SQL Server R Services のユーザー アカウントをプロビジョニングする  
 R の実行時プロセスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 特権の低いローカル ユーザー アカウントのコンテキストで実行します。 特権の低い個々のアカウントで R のランタイム プロセスを実行すると、次の利点があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のコンピューターで実行されている R のランタイム プロセスの特権が少なくなります  
  
-   R のランタイム セッション間が分離されます  
  
 インストール プロセスの一部として [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], 、新しい Windows *ユーザー アカウントのプール* が作成される R ランタイム プロセスの実行に必要なローカル ユーザー アカウントが含まれます。 R. をサポートするために必要な場合は、ユーザーの数を変更することができます。データベース管理者は、R のサービスが有効になっている任意のインスタンスに接続するには、このグループ権限を与える必要があります。 詳細については、次を参照してください。 [SQL Server の R のサービスのユーザー アカウントのプールを変更](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md)します。  
  
 ただし、アクセス制御リスト (ACL) に定義できる機密性の高いリソースに対して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] R ランタイム プロセスがリソースへのアクセスを取得することを防ぐには、このグループにアクセスを拒否します。  
  
-   ユーザー アカウントのプールは、特定のインスタンスにリンクされます。  インスタンスごとにどの R のスクリプトが有効になって、個々 のプールのワーカーのアカウントが作成されます。 アカウントは、インスタンス間で共有できません。
  
-   プールのユーザー アカウント名は、SQLInstanceName*nn*の形式になります。 たとえば、既定のインスタンスを R サーバーとして使用している場合、ユーザー アカウント プールは MSSQLSERVER01、MSSQLSERVER02 といったアカウント名をサポートします。  
  
-   ユーザー アカウント プールのサイズは静的であり、既定値は 20 です。 同時に起動できる R のランタイム セッションの数は、このユーザー アカウント プールのサイズによって制限されます。 ただし、この制限は、SQL Server 構成マネージャーを使用して、管理者によって変更できます。  
  
  
 ユーザー アカウント プールを変更する方法の詳細については、「 [Modify the User Account Pool for SQL Server R Services](../../advanced-analytics/r-services/modify-the-user-account-pool-for-sql-server-r-services.md)」を参照してください。  
  
##  <a name="bkmk_ManagingMemory"></a> R プロセスによるメモリの使用を管理する  
 既定により、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] に関連付けられた R のランタイム プロセスは合計マシン メモリの 20% を超えて使用しないように制限されています。 ただし、必要に応じて、管理者がこの制限を増やすことができます。  
  
 一般に、この時間がモデルのトレーニング データの多くの行に予測するなど、深刻な R タスクに適していないができます。 予約されるメモリの量を削減する必要があります [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (またはその他のサービス) を使用してリソース ガバナーを外部のリソース プールまたはプールを定義し、割り当てます。 詳細については、次を参照してください。 [R サービスのリソース管理](../../advanced-analytics/r-services/resource-governance-for-r-services.md)します。  
  
##  <a name="bkmk_ChangingConfig"></a> 構成ファイルを使用して、高度なサービス オプションを変更します。  
 
一部の高度なプロパティを制御する [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] を編集して、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] 構成ファイル。 このファイルは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ中に作成され、既定では、次の場所にプレーン テキスト ファイルとして保存されます。  
 
```  
<instance path>\binn\rlauncher.config  
```  
  
 このファイルを変更するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューターの管理者になる必要があります。 ファイルを編集する場合は、変更を保存する前に、バックアップ コピーを作成することをお勧めします。  
  
 たとえば、メモ帳を使って既定のインスタンス (MSSQLSERVER) の構成ファイルを開くには、管理者としてコマンド プロンプトを開き、次のコマンドを入力します。  
  
```  
C:\>Notepad.exe "%programfiles%\Microsoft SQL Server\MSSQL13.MSSQLSERVER\mssql\binn\rlauncher.config"  
  
```  
  
###  <a name="bkmk_properties"></a> 構成プロパティ  
 すべての設定が、キーと値のペアの形をとり、各設定は個別の行に表示されます。 たとえば、このプロパティは、システム メモリの 20% 未満が R のプロセスで使用されることを指定します。  
  
 既定値: `MEMORY_LIMIT_PERCENT=20`  
  
 次の表のサポートされている設定の各 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], 、許容される値を使用しています。  
  
|設定名|[値の型]|既定値|説明|  
|------------------|----------------|-------------|-----------------|  
|JOB_CLEANUP_ON_EXIT|Integer<br /><br /> 0 = 無効<br /><br /> 1 = 有効|1<br /><br /> 終了時にログ ファイルが削除されます|各 R セッションに作成された一時作業フォルダーを R セッションの完了後にクリーンアップするかどうかを指定します。 この設定はデバッグに便利です。<br /><br /> 注: これは内部でのみ設定されます。この値を変更しないでください。|  
|TRACE_LEVEL|Integer<br /><br /> 1 = エラー<br /><br /> 2 = パフォーマンス<br /><br /> 3 = 警告<br /><br /> 4 = 情報|1<br /><br /> 警告のみ出力します|デバッグのための R ランチャー (MSSQLLAUNCHPAD) のトレースの詳細レベルを構成します。 この設定は、次のトレース ファイルに格納されているトレースの詳細に影響します。どちらも LOG_DIRECTORY 設定で指定されたパスにあります。<br /><br /> **rlauncher.log**: T-SQL クエリで起動した R セッションに対して生成されるトレース ファイル。<br /><br /> このシナリオの詳細については、「 [Data Exploration and Predictive Modeling with R](../../advanced-analytics/r-services/data-exploration-and-predictive-modeling-with-r.md)」を参照してください。|  

## <a name="bkmk_Launchpad"></a>スタート パッド サービス アカウントを変更します。

個別の [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] サービスが構成した各インスタンスに対して作成された [!INCLUDE[rsql_productname_md](../../includes/rsql-productname-md.md)]します。 

既定では、スタート パッドは R スクリプトを実行するすべての必要なアクセス許可を持つようにプロビジョニングされている NT Service\MSSQLLaunchpad、アカウントを使用して実行するように構成します。 ただし、このアカウントを変更する場合、スタート パッドできないことがあります開始するか、R スクリプトを実行する SQL Server インスタンスにアクセスします。
 
  サービス アカウントを変更した場合は、使用することを確認される、 **ローカル セキュリティ ポリシー** 各サービスのアクセス許可がアカウントにこれらのアクセス許可を含めるアプリケーションと更新プログラム。
  + プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)
  + スキャン チェックを行わない (SeChangeNotifyPrivilege)
  + サービスとしてログオン (SeServiceLogonRight)
  + プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)

SQL Server サービスの実行に必要なアクセス許可の詳細については、次を参照してください。 [Windows サービス アカウントの構成とアクセス許可](https://msdn.microsoft.com/library/ms143504.aspx#Windows)します。
   
## 参照  
 [SQL Server R Services の概要](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)  
  
  