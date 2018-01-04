---
title: "SQL Server の機械学習のユーザー アカウント プールを変更する |Microsoft ドキュメント"
ms.date: 11/03/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58b79170-5731-46b5-af8c-21164d28f3b0
caps.latest.revision: "19"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: Inactive
ms.openlocfilehash: 0cd54371d35595dfbef6f54fcd66dab8d2dd812f
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="modify-the-user-account-pool-for-sql-server-machine-learning"></a>SQL Server の機械学習のユーザー アカウント プールを変更します。

[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] サービスによるタスクの実行をサポートするために、[!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)] のインストール プロセスの一部として、新しい Windows "ユーザー アカウント プール" が作成されました。** これらのワーカー アカウントの目的は、別の SQL ユーザーの外部のスクリプトの同時実行を分離します。

この記事では、既定の構成、セキュリティ、および容量のワーカー アカウント、および既定の構成を変更する方法について説明します。

**適用されます:** [!INCLUDE[sssql15-md](../../includes/sssql15-md.md)] [!INCLUDE[rsql-productname-md](../../includes/rsql-productname-md.md)]、 [!INCLUDE[sscurrent-md](../../includes/sscurrent-md.md)][!INCLUDE[rsql-productnamenew-md](../../includes/rsql-productnamenew-md.md)]

## <a name="worker-accounts-used-for-external-script-execution"></a>外部スクリプトの実行に使用されるワーカー アカウント

によって Windows アカウント グループが作成された[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]学習をインストールして有効にするコンピューターは、各インスタンスをセットアップします。

-   既定のインスタンスでは、グループ名は **SQLRUserGroup** です。 名前は、R、Python またはその両方を使用するかどうかは同じです。
-   名前付きインスタンスでは、既定のグループ名にインスタンス名が付加されます: たとえば、 **SQLRUserGroupMyInstanceName**。

既定では、ユーザー アカウント プールには 20 個のユーザー アカウントが含まれています。 ほとんどの場合、20 以上の機械学習タスクをサポートするために十分ながアカウントの数を変更することができます。
-  既定のインスタンスでは、個々のアカウントは **MSSQLSERVER01** ～ **MSSQLSERVER20** と命名されます。
-   名前付きインスタンスの場合、個々のアカウントはインスタンス名に基づいて命名されます。たとえば、 **MyInstanceName01** ～ **MyInstanceName20**。

複数のインスタンスは、機械学習を使用している場合、コンピューターは、複数のユーザー グループがあります。 グループは、インスタンスで共有することはできません。

### <a name = "HowToChangeGroup"></a>ワーカー アカウントの数を変更する方法

アカウント プール内のユーザー数を変更するには、以下に示すように、[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] サービスのプロパティを編集する必要があります。

各ユーザー アカウントに関連付けられるパスワードはランダムに生成されますが、アカウントの作成後に変更することもできます。

1. SQL Server 構成マネージャーを開き、**[SQL Server のサービス]** をクリックします。
2. SQL Server スタート パッド サービスをダブルクリックし、サービスが実行されている場合は、サービスを停止します。
3.  **[サービス]** タブで、[開始モード] が [自動] に設定されていることを確認します。 スタート パッドが実行されていない場合、外部スクリプトを開始できません。
4.  **[詳細設定]** タブをクリックし、必要であれば、**[外部ユーザーの数]** の値を編集します。 この設定で制御さまざまな SQL ユーザーの数ことができます外部スクリプト実行セッションを同時にします。 既定では 20 アカウントです。
5. パスワードを定期的に変更するポリシーが組織で実施されている場合は、オプションで、**[外部ユーザーのパスワードのリセット]** を _[はい]_ に設定できます。 これを行うと、ユーザー アカウントに対してスタート パッドが保持している暗号化パスワードが再生成されます。 詳しくは、「[パスワード ポリシーの実施](#bkmk_EnforcePolicy)」をご覧ください。
6.  スタート パッド サービスを再起動します。

## <a name="managing-machine-learning-workloads"></a>Machine learning のワークロードを管理します。

このプール内のアカウントの数では、外部スクリプトの数のセッション同時実行が可能かを決定します。  既定では、20 アカウントが作成された、20 の異なるユーザーがアクティブの R または Python セッション一度に 1 つを持つことを意味します。 20 を超える同時スクリプトを実行する予定の場合は、ワーカー アカウントの数を増やすことができます。

同じユーザーでは、同時に複数の外部スクリプトを実行するとき、セッションがそのユーザーが実行すべてワーカーと同じアカウントを使用します。 たとえば、1 人のユーザーには、リソースは許可されてがすべてのスクリプトは、1 つのワーカー アカウントを使用して実行は限りが同時に実行 100 の異なる R スクリプトがあります。

次のようにサポートできますが、ワーカー アカウントの数と、1 人のユーザーが実行できる、同時セッションの数は、サーバーのリソースによってのみ制限されます。 通常、R ランタイムの使用時に遭遇する最初のボトルネックは、メモリです。

Python または R スクリプトで使用できるリソースは、SQL Server によって管理されます。 SQL Server の DMV を使用してリソースの使用状況を監視するか、または関連する Windows ジョブ オブジェクトのパフォーマンス カウンターを見て、サーバー メモリの使用量を必要に応じて調整することをお勧めします。 SQL Server Enterprise Edition がある場合は、構成することによって外部スクリプトを実行するために使用されているリソースを割り当てることができます、[外部リソース プール](../../advanced-analytics/r-services/how-to-create-a-resource-pool-for-r.md)です。

マシンの管理に関する詳細について学習のタスクの容量、以下を参照します。

- [R Services の SQL Server の構成](../../advanced-analytics/r/sql-server-configuration-r-services.md)
-  [R Services のパフォーマンスのケース スタディ](../../advanced-analytics/r/performance-case-study-r-services.md)

## <a name="security"></a>Security

各ユーザー グループは、特定のインスタンス上の [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] サービスに関連付けられます。他のインスタンス上で実行されている R ジョブをサポートすることはできません。

セッションがアクティブなときには、各ワーカー アカウントに対して一時フォルダーが作成されます。一時フォルダーには、R スクリプトの実行時に R と SQL Server によって使用される、スクリプト オブジェクト、中間結果、およびその他の情報が格納されます。 これらの作業ファイル (ExtensibilityData フォルダーの下に置かれます) は、アクセスが管理者のみに制限され、SQL Server スクリプトの完了後にクリーンアップされます。 

詳しくは、「[Security Overview](../../advanced-analytics/r-services/security-overview-sql-server-r.md)」(セキュリティの概要) をご覧ください。

### <a name="bkmk_EnforcePolicy"></a>パスワード ポリシーの実施

パスワードを定期的に変更するポリシーが組織で実施されている場合は、ユーザー アカウントに対してスタート パッドが保持している暗号化パスワードを、強制的に再生成しなければならない場合があります。  

この設定を有効にし、パスワードの更新を強制するには、SQL Server 構成マネージャーでスタート パッド サービスの **[プロパティ]** ペインを開き、**[詳細設定]** をクリックして、**[外部ユーザーのパスワードのリセット]** を **[はい]** に変更します。 この変更を適用すると、すべてのユーザー アカウントのパスワードが直ちに再生成されます。 この変更後に R スクリプトを使用するには、スタート パッド サービスを再起動する必要があります。これにより、新しく生成されたパスワードが読み取られたます。 

パスワードを定期的にリセットするには、このフラグを手動で設定するか、スクリプトを使用します。

### <a name="additional-permission-required-to-support-remote-compute-contexts"></a>リモートの計算コンテキストをサポートするために必要な追加権限

既定では、R ワーカー アカウントのグループには、それが関連付けられている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに対するログイン権限が**ありません**。 そのため、リモート クライアントから SQL Server に接続して R スクリプトを実行するユーザーが いる場合や、ODBC を使用して追加データを取得するスクリプトがある場合には、問題が生じる場合があります。 

これらのシナリオをサポートする必要がある場合、データベース管理者は、R スクリプトが実行される SQL Server インスタンスへのログイン権限 (**Connect to** 権限) を、R ワーカー アカウントのグループに提供する必要があります。 これを呼びます*黙示的な認証*、により、SQL Server のリモート ユーザーの資格情報を使用して R スクリプトを実行するとします。

> [!NOTE]
> SQL ログインを利用し、リモート ワークステーションから R スクリプトを実行する場合、この制限は適用されません。SQL ログインの資格情報は、R クライアントから SQL Server インスタンスに、それから ODBC に明示的に渡されるためです。


### <a name="how-to-enable-implied-authentication"></a>暗黙の認証を有効にする方法

1. R または Python コードを実行するインスタンスの管理者として SQL Server Management Studio を開きます。

2. 次のスクリプトを実行します。 ユーザー グループの名前 (既定値を変更した場合) と、コンピューターとインスタンスの名前を必ず編集してください。

    ```sql
    USE [master]
    GO
    
    CREATE LOGIN [computername\SQLRUserGroup] FROM WINDOWS WITH DEFAULT_DATABASE=[master], DEFAULT_LANGUAGE=[language]
    GO
    ````

