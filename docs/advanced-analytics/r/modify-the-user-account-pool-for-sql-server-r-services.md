---
title: "SQL Server R Services のユーザー アカウント プールを変更する | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58b79170-5731-46b5-af8c-21164d28f3b0
caps.latest.revision: 19
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 33e22f7edec807d046798d89a9cd5daa642e8d3b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="modify-the-user-account-pool-for-sql-server-r-services"></a>SQL Server R サービスのユーザー アカウント プールを変更する
  [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] サービスによるタスクの実行をサポートするために、[!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] のインストール プロセスの一部として、新しい Windows "ユーザー アカウント プール" が作成されました。** これらのワーカー アカウントの目的は、異なる SQL ユーザーによる R スクリプトの同時実行を隔離することです。 

このトピックでは、ワーカー アカウントの既定の構成、セキュリティおよび容量と、既定の構成の変更方法について説明します。

## <a name="worker-accounts-used-by-r-services"></a>R Services によって使用されるワーカー アカウント   

Windows アカウント グループは、R Services がインストールされている各インスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セットアップによって作成されます。 そのため、R をサポートするインスタンスを複数インストールした場合は、複数のユーザー グループが作成されます。

-   既定のインスタンスでは、グループ名は **SQLRUserGroup** です。 
-   名前付きインスタンスでは、既定のグループ名にインスタンス名が付加されます: たとえば、 **SQLRUserGroupMyInstanceName**。 

既定では、ユーザー アカウント プールには 20 個のユーザー アカウントが含まれています。 ほとんどの場合は、20 個で R セッションを十分サポートできますが、アカウント数を変更することもできます。
-  既定のインスタンスでは、個々のアカウントは **MSSQLSERVER01** ～ **MSSQLSERVER20** と命名されます。  
-   名前付きインスタンスの場合、個々のアカウントはインスタンス名に基づいて命名されます。たとえば、 **MyInstanceName01** ～ **MyInstanceName20**。  

### <a name = "HowToChangeGroup"> </a>R ワーカー アカウントの数を変更する方法

アカウント プール内のユーザー数を変更するには、以下に示すように、[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] サービスのプロパティを編集する必要があります。  
  
各ユーザー アカウントに関連付けられるパスワードはランダムに生成されますが、アカウントの作成後に変更することもできます。  
  
1. SQL Server 構成マネージャーを開き、**[SQL Server のサービス]** をクリックします。
2. SQL Server スタート パッド サービスをダブルクリックし、サービスが実行されている場合は、サービスを停止します。 
3.  **[サービス]** タブで、[開始モード] が [自動] に設定されていることを確認します。 スタート パッドが実行されていない場合、R スクリプトは失敗します。
4.  **[詳細設定]** タブをクリックし、必要であれば、**[外部ユーザーの数]** の値を編集します。 この設定は、R でクエリを同時に実行できる SQL ユーザーの数 を制御します。既定値は、20 アカウントです。
5. パスワードを定期的に変更するポリシーが組織で実施されている場合は、オプションで、**[外部ユーザーのパスワードのリセット]** を _[はい]_ に設定できます。 これを行うと、ユーザー アカウントに対してスタート パッドが保持している暗号化パスワードが再生成されます。 詳しくは、「[パスワード ポリシーの実施](#bkmk_EnforcePolicy)」をご覧ください。    
6.  サービスを再起動します。  

## <a name="managing-r-workload"></a>R のワークロードの管理

このプール内のユーザー アカウント数によって、同時にアクティブにできる R セッションの数が決まります。  既定では、20 個のアカウントが作成されます。つまり、20 人のユーザーが、アクティブな R セッションを同時に利用することができます。 より多くのユーザーが R スクリプトを同時に実行することが予想される場合は、ワーカー アカウントの数を増やすこともできます。 

同じユーザーが複数の R スクリプトを同時に実行した場合、そのユーザーが実行したセッションにはすべて、同じワーカー アカウントが使用されます。 たとえば、1 人のユーザーが 100 個のスクリプトを同時に実行した場合は、リソースが許す限り、1 つのワーカー アカウントが使用されます。

サポートできるワーカー アカウントの数と、1 人のユーザーが同時に実行できる R セッションの数は、サーバーのリソースによってのみ制限されます。  通常、R ランタイムの使用時に遭遇する最初のボトルネックは、メモリです。

R Services では、R スクリプトで使用できるリソースは SQL Server によって管理されます。 SQL Server の DMV を使用してリソースの使用状況を監視するか、または関連する Windows ジョブ オブジェクトのパフォーマンス カウンターを見て、サーバー メモリの使用量を必要に応じて調整することをお勧めします。 
 
SQL Server Enterprise Edition を使用している場合は、[外部リソース プール](../../advanced-analytics/r-services/how-to-create-a-resource-pool-for-r.md)を構成することで、R スクリプトの実行に使用されるリソースを割り当てることができます。 

R スクリプトの容量管理について詳しくは、次の記事をご覧ください。

- [R Services 用の SQL Server の構成](../../advanced-analytics/r-services/sql-server-configuration-r-services.md)
-  [R Services のパフォーマンス ケース スタディ](../../advanced-analytics/r-services/performance-case-study-r-services.md)

## <a name="security"></a>セキュリティ

各ユーザー グループは、特定のインスタンス上の [!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)] サービスに関連付けられます。他のインスタンス上で実行されている R ジョブをサポートすることはできません。

セッションがアクティブなときには、各ワーカー アカウントに対して一時フォルダーが作成されます。一時フォルダーには、R スクリプトの実行時に R と SQL Server によって使用される、スクリプト オブジェクト、中間結果、およびその他の情報が格納されます。 これらの作業ファイル (ExtensibilityData フォルダーの下に置かれます) は、アクセスが管理者のみに制限され、SQL Server スクリプトの完了後にクリーンアップされます。 

詳しくは、「[Security Overview](../../advanced-analytics/r-services/security-overview-sql-server-r.md)」(セキュリティの概要) をご覧ください。

### <a name="bkmk_EnforcePolicy"></a>パスワード ポリシーの実施

パスワードを定期的に変更するポリシーが組織で実施されている場合は、ユーザー アカウントに対してスタート パッドが保持している暗号化パスワードを、強制的に再生成しなければならない場合があります。  

この設定を有効にし、パスワードの更新を強制するには、SQL Server 構成マネージャーでスタート パッド サービスの **[プロパティ]** ペインを開き、**[詳細設定]** をクリックして、**[外部ユーザーのパスワードのリセット]** を **[はい]** に変更します。 この変更を適用すると、すべてのユーザー アカウントのパスワードが直ちに再生成されます。 この変更後に R スクリプトを使用するには、スタート パッド サービスを再起動する必要があります。これにより、新しく生成されたパスワードが読み取られたます。 

パスワードを定期的にリセットするには、このフラグを手動で設定するか、スクリプトを使用します。

### <a name="additional-permission-required-to-support-remote-compute-contexts"></a>リモートの計算コンテキストをサポートするために必要な追加権限

既定では、R ワーカー アカウントのグループには、それが関連付けられている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに対するログイン権限が**ありません**。 そのため、リモート クライアントから SQL Server に接続して R スクリプトを実行するユーザーが いる場合や、ODBC を使用して追加データを取得するスクリプトがある場合には、問題が生じる場合があります。 

これらのシナリオをサポートする必要がある場合、データベース管理者は、R スクリプトが実行される SQL Server インスタンスへのログイン権限 (**Connect to** 権限) を、R ワーカー アカウントのグループに提供する必要があります。 これは*暗黙の認証*と呼ばれ、これにより SQL Server は、リモート ユーザーの資格情報を使用して R スクリプトを実行できるようになります。

> [!NOTE]
> SQL ログインを利用し、リモート ワークステーションから R スクリプトを実行する場合、この制限は適用されません。SQL ログインの資格情報は、R クライアントから SQL Server インスタンスに、それから ODBC に明示的に渡されるためです。


### <a name="how-to-enable-implied-authentication"></a>暗黙の認証を有効にする方法

1. R コードを実行するインスタンスで、SQL Server Management Studio を監理者として開きます。

2. 次のスクリプトを実行します。 ユーザー グループの名前 (既定値を変更した場合) と、コンピューターとインスタンスの名前を必ず編集してください。

    ```sql
    USE [master]
    GO
    
    CREATE LOGIN [computername\SQLRUserGroup] FROM WINDOWS WITH DEFAULT_DATABASE=[master], DEFAULT_LANGUAGE=[language]
    GO  
    ````


  
## <a name="see-also"></a>参照  
 [構成 (SQL Server R Services)](../../advanced-analytics/r-services/configuration-sql-server-r-services.md)
  

