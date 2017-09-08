---
title: "Machine Learning のサービスの構成オプションの詳細 |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 11/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d73fd98-0c61-4a62-94bb-75658195f2a6
caps.latest.revision: 21
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 872acf107d72989b4623a9d5f4ccb85c44d1f2f9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="advanced-configuration-options-for-machine-learning-services"></a>Machine Learning のサービスの構成オプションの詳細

この記事では、行うことができますのセットアップ後に、R ランタイムと SQL Server での機械学習に関連付けられているその他のサービスの構成を変更する変更について説明します。

適用されます SQL Server 2016 の R Services、SQL Server 2017 機械学習のサービス。

##  <a name="bkmk_Provisioning"></a>ユーザーのプロビジョニング アカウントのマシンの学習

外部スクリプトのプロセスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]特権の低いローカル ユーザー アカウントのコンテキストで実行します。 個々 の低特権アカウントでこれらのプロセスを実行すると、次の利点があります。

+ 外部スクリプトのランタイム プロセスの特権を減らすことが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンピューター
+ R、Python などの外部のランタイム セッション間が分離を提供します。

新しい Windows のセットアップの一部として*ユーザー アカウント プール*が作成された R ランタイム プロセスを実行するために必要なローカル ユーザー アカウントを格納しています。 R をサポートする必要がある場合は、ユーザーの数を変更できます。データベース管理者はこのグループに、R Services が有効になっているインスタンスに接続する権限を与える必要があります。 詳細については、「 [Modify the User Account Pool for SQL Server R Services](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)に関連するその他のサービスの構成に軽微な変更を行うことができます。

一方、アクセス制御リスト (ACL) を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機密リソースに定義してこのグループへのアクセスを拒否することで、R のランタイム プロセスがこのリソースにアクセスすることを防ぐことができます。

+ ユーザー アカウント プールは、特定のインスタンスにリンクされます。  R スクリプトが有効になっているインスタンスごとに、ワーカー アカウントのプールが個別に作成されます。 インスタンス間でアカウントを共有することはできません。

+ プールのユーザー アカウント名は、SQLInstanceName*nn*に関連するその他のサービスの構成に軽微な変更を行うことができます。 たとえば、既定のインスタンスを R サーバーとして使用している場合、ユーザー アカウント プールは MSSQLSERVER01、MSSQLSERVER02 といったアカウント名をサポートします。

+ ユーザー アカウント プールのサイズは静的であり、既定値は 20 です。 同時に起動できる R のランタイム セッションの数は、このユーザー アカウント プールのサイズによって制限されます。 ただし、この制限は、管理者が SQL Server 構成マネージャーを使用して変更できます。

ユーザー アカウント プールを変更する方法の詳細については、「 [Modify the User Account Pool for SQL Server R Services](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)」を参照してください。

##  <a name="bkmk_ManagingMemory"></a>外部スクリプトのプロセスによって使用されるメモリを管理します。

既定により、 [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] に関連付けられた R のランタイム プロセスは合計マシン メモリの 20% を超えて使用しないように制限されています。 ただし、必要に応じて、管理者がこの制限を増やすことができます。

一般に、モデルのトレーニングや多数のデータ行に基づく予測などの重要な R タスクには、この量では不十分です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (または他のサービス) に予約されたメモリの量を削減し、Resource Governor を使用して外部のリソース プールを定義し、メモリを割り当てることが必要な場合があります。 詳細については、次を参照してください。 [R のリソース管理](../../advanced-analytics/r/resource-governance-for-r-services.md)です。

##  <a name="bkmk_ChangingConfig"></a>構成ファイルを使用して高度なサービス オプションを変更します。

[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] の構成ファイルを編集すると、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] の高度なプロパティの一部を制御できます。 このファイルは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ中に作成され、既定では、次の場所にプレーン テキスト ファイルとして保存されます。

`<instance path>\binn\rlauncher.config`

このファイルを変更するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューターの管理者になる必要があります。 ファイルを編集する場合は、変更を保存する前に、バックアップ コピーを作成することをお勧めします。

たとえばを開くには、既定のインスタンスの構成ファイルをメモ帳を使用するのには管理者としてコマンド プロンプトを開きますして次のコマンドを入力します。

```
C:\>Notepad.exe "%programfiles%\Microsoft SQL Server\MSSQL13.MSSQLSERVER\mssql\binn\rlauncher.config"  
```

##  <a name="bkmk_properties"></a>構成プロパティを編集します。

次の表は、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] でサポートされる各設定と、使用可能な値を示しています。

すべての設定が、キーと値のペアの形をとり、各設定は個別の行に表示されます。 たとえば、このプロパティは、RLauncher のトレース レベルを指定します。

既定値: TRACE_LEVEL=4


|**設定名**|**[値の型]**|**既定値**|**説明**|
|------------------|----------------|-------------|-----------------|
|JOB_CLEANUP_ON_EXIT|Integer<br /><br /> 0 = 無効<br /><br /> 1 = 有効|1<br /><br /> 終了時にログ ファイルが削除されます|各 R セッションに作成された一時作業フォルダーを R セッションの完了後にクリーンアップするかどうかを指定します。 この設定はデバッグに便利です。<br /><br /> 注: これは内部でのみ設定されます。この値を変更しないでください。|
|TRACE_LEVEL|Integer<br /><br /> 1 = エラー<br /><br /> 2 = パフォーマンス<br /><br /> 3 = 警告<br /><br /> 4 = 情報|1<br /><br /> 警告のみ出力します|デバッグのための R ランチャー (MSSQLLAUNCHPAD) のトレースの詳細レベルを構成します。 この設定は、次のトレース ファイルに格納されているトレースの詳細に影響します。どちらも LOG_DIRECTORY 設定で指定されたパスにあります。<br /><br /> **rlauncher.log**: T-SQL クエリで起動した R セッションで生成されるトレース ファイル。<br /><br /> |

## <a name="bkmk_Launchpad"></a>スタート パッド サービス アカウントを変更します。

個別の[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]機械学習サービスを構成した各インスタンスのサービスが作成されます。

既定では、スタート パッドは NT Service\MSSQLLaunchpad のアカウントを使用して実行するように構成され、このアカウントには、R スクリプトの実行に必要なすべてのアクセス許可がプロビジョニングされています。 ただし、このアカウントを変更する場合、スタート パッドできないことがありますを起動したり、外部スクリプトを実行可能な SQL Server インスタンスにアクセスします。

サービス アカウントを変更する場合は、**ローカル セキュリティ ポリシー** アプリケーションを使用し、各サービス アカウントのアクセス許可を更新して以下のアクセス許可を追加します。

+ プロセスに対してメモリ クォータを調整する (SeIncreaseQuotaPrivilege)
+ スキャン チェックを行わない (SeChangeNotifyPrivilege)
+ サービスとしてログオン (SeServiceLogonRight)
+ プロセス レベル トークンを置き換える (SeAssignPrimaryTokenPrivilege)

SQL Server サービスの実行に必要なアクセス許可の詳細については、「[Configure Windows Service Accounts and Permissions (Windows サービス アカウントとアクセス許可の構成)](https://msdn.microsoft.com/library/ms143504.aspx#Windows)」をご覧ください。

## <a name="see-also"></a>参照

[セキュリティに関する考慮事項](security-considerations-for-the-r-runtime-in-sql-server.md)
