---
title: "マージ アーティクルのビジネス ロジック ハンドラーの実装 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "マージ レプリケーションの競合回避 [SQL Server レプリケーション]、ビジネス ロジック ハンドラー"
  - "マージ レプリケーションのビジネス ロジック ハンドラー [SQL Server レプリケーション]"
  - "競合回避 [SQL Server レプリケーション]、マージ レプリケーション"
  - "ビジネス ロジック ハンドラー [SQL Server レプリケーション]"
  - "BusinessLogicModule クラス"
ms.assetid: ed477595-6d46-4fa2-b0d3-a5358903ec05
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# マージ アーティクルのビジネス ロジック ハンドラーの実装
  このトピックでは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] でレプリケーション プログラミングまたはレプリケーション管理オブジェクト (RMO) を使用して、マージ アーティクルにビジネス ロジック ハンドラーを実装する方法について説明します。  
  
  <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> 名前空間は、マージ レプリケーションの同期処理中に発生するイベントを処理する複雑なビジネス ロジックを記述することができますインターフェイスを実装します。 ビジネス ロジック ハンドラーのメソッドは、同期中にレプリケートされる変更行ごとに、レプリケーション処理から呼び出すことができます。  
  
 ビジネス ロジック ハンドラーを実装するための一般的な手順を次に示します。  
  
1.  ビジネス ロジック ハンドラーのアセンブリを作成します。  
  
2.  ディストリビューターにアセンブリを登録します。  
  
3.  マージ エージェントが実行されるサーバーにアセンブリを配置します。 プル サブスクリプションの場合、エージェントはサブスクライバー上で実行されます。プッシュ サブスクリプションの場合、エージェントはディストリビューター上で実行されます。 Web 同期を使用した場合、エージェントは Web サーバー上で実行されます。  
  
4.  ビジネス ロジック ハンドラーを使用するアーティクルを作成するか、またはビジネス ロジック ハンドラーを使用する既存のアーティクルを変更します。  
  
 指定するビジネス ロジック ハンドラーは、同期されるすべての行に対して実行されます。 その他のアプリケーションまたはネットワーク サービスに対する複雑なロジックおよび呼び出しは、パフォーマンスに影響を与える可能性があります。 ビジネス ロジック ハンドラーの詳細については、次を参照してください。 [マージ同期中にビジネス ロジックを実行](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)します。  
  
 **このトピックの内容**  
  
-   **マージ アーティクルにビジネス ロジック ハンドラーを実装するために使用するもの:**  
  
     [レプリケーション プログラミング](#ReplProg)  
  
     [レプリケーション管理オブジェクト (RMO)](#RMOProcedure)  
  
##  <a name="ReplProg"></a> レプリケーション プログラミングの使用  
  
#### ビジネス ロジック ハンドラーを作成および配置するには  
  
1.  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio で、.NET アセンブリの新しいプロジェクトを作成し、ビジネス ロジック ハンドラーの実装コードを記述します。  
  
2.  次の名前空間の参照をプロジェクトに追加します。  
  
    |アセンブリ参照|場所|  
    |------------------------|--------------|  
    |<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM (既定インストール)|  
    |<xref:System.Data>|GAC (.NET Framework のコンポーネント)|  
    |<xref:System.Data.Common>|GAC (.NET Framework のコンポーネント)|  
  
3.  オーバーライドするクラスを追加、 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> クラスです。  
  
4.  実装、 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> プロパティを処理対象の変更の種類を示します。  
  
5.  1 つ以上の次のメソッドのオーバーライド、 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> クラス。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> -同期中にデータの変更がコミットされたときに呼び出されます。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> のアップロードまたはダウンロードと DELETE ステートメント エラーが発生すると呼び出されます。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> -DELETE ステートメントがされているときに呼び出されるアップロードまたはダウンロードします。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> のアップロードまたはダウンロード時に、INSERT ステートメントにエラーが発生すると呼び出されます。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> -INSERT ステートメントがされているときに呼び出されるアップロードまたはダウンロードします。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> -パブリッシャーとサブスクライバーで UPDATE ステートメントの競合が発生するときに呼び出されます。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> -UPDATE ステートメントがパブリッシャーとサブスクライバーの DELETE ステートメントと競合する場合に呼び出されます。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> のアップロードまたはダウンロード時に、UPDATE ステートメントにエラーが発生すると呼び出されます。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> -UPDATE ステートメントがされているときに呼び出されるアップロードまたはダウンロードします。  
  
6.  プロジェクトをビルドして、ビジネス ロジック ハンドラー アセンブリを作成します。  
  
7.  アセンブリを、マージ エージェント実行可能ファイル (replmerg.exe) を含むディレクトリ (既定のインストールの場合は [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM) に配置するか、.NET グローバル アセンブリ キャッシュ (GAC) にインストールします。 マージ エージェント以外のアプリケーションがアセンブリへのアクセスを必要とする場合は、アセンブリを GAC にのみインストールしてください。 アセンブリをグローバル アセンブリ キャッシュ ツールを使用して GAC にインストールすることができます (**Gacutil.exe)** は .NET Framework SDK で提供します。  
  
    > [!NOTE]  
    >  ビジネス ロジック ハンドラーは、Web 同期を使用するときに replisapi.dll をホストする IIS サーバーなど、マージ エージェントを実行する各サーバーに配置する必要があります。  
  
#### ビジネス ロジック ハンドラーを登録するには  
  
1.  パブリッシャーで実行 [sp_enumcustomresolvers & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) アセンブリが既に登録されていないことと、ビジネス ロジック ハンドラーを確認します。  
  
2.  ディストリビューターで実行 [sp_registercustomresolver & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md), 、ビジネス ロジック ハンドラーのフレンドリ名を指定する **@article_resolver**, の値 **true** の **@is_dotnet_assembly**, のアセンブリの名前 **@dotnet_assembly_name**, 、およびオーバーライドするクラスの完全修飾名 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> の **@dotnet_class_name**します。  
  
    > [!NOTE]  
    >  起動する場合、アセンブリは、マージ エージェント実行可能ファイルと同じディレクトリに配置されている、アプリケーションと同じディレクトリを同期的にマージ エージェント、または、グローバル アセンブリ キャッシュ (GAC) 内のアセンブリ名を持つ完全なパスを指定する必要があります。 **@dotnet_assembly_name**します。 Web 同期を使用する場合は、Web サーバーでアセンブリの位置を指定する必要があります。  
  
#### 新しいテーブル アーティクルでビジネス ロジック ハンドラーを使用するには  
  
1.  実行 [sp_addmergearticle & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) ビジネス ロジック ハンドラーのフレンドリ名を指定するアーティクルを定義する **@article_resolver**します。 詳しくは、「 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
#### 既存のテーブル アーティクルでビジネス ロジック ハンドラーを使用するには  
  
1.  実行 [sp_changemergearticle & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), を指定して **@publication**, 、**@article**, の値 **article_resolver** の **@property**, とビジネス ロジック ハンドラーの表示名 **@value**します。  
  
###  <a name="TsqlExample"></a> 例 (レプリケーション プログラミング)  
 次の例に、監査ログを作成するビジネス ロジック ハンドラーを示します。  
  
 [!code-csharp[HowTo#rmo_BusinessLogicCode](../../relational-databases/replication/codesnippet/csharp/rmohowto/businesslogic.cs#rmo_businesslogiccode)]  
  
 [!code-vb[HowTo#rmo_vb_BusinessLogicCode](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/businesslogic.vb#rmo_vb_businesslogiccode)]  
  
 次の例では、ビジネス ロジック ハンドラー アセンブリをディストリビューターに登録し、カスタム ビジネス ロジックを使用するように既存のマージ アーティクルを変更します。  
  
 [!code-sql[HowTo#sp_RegisterBLH_10](../../relational-databases/replication/codesnippet/tsql/implement-a-business-log_3.sql)]  
  
##  <a name="RMOProcedure"></a> レプリケーション管理オブジェクト (RMO) の使用  
  
#### ビジネス ロジック ハンドラーを作成するには  
  
1.  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio で、.NET アセンブリの新しいプロジェクトを作成し、ビジネス ロジック ハンドラーの実装コードを記述します。  
  
2.  次の名前空間の参照をプロジェクトに追加します。  
  
    |アセンブリ参照|場所|  
    |------------------------|--------------|  
    |<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM (既定インストール)|  
    |<xref:System.Data>|GAC (.NET Framework のコンポーネント)|  
    |<xref:System.Data.Common>|GAC (.NET Framework のコンポーネント)|  
  
3.  オーバーライドするクラスを追加、 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> クラスです。  
  
4.  実装、 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> プロパティを処理対象の変更の種類を示します。  
  
5.  1 つ以上の次のメソッドのオーバーライド、 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> クラス。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> -同期中にデータの変更がコミットされたときに呼び出されます。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> -DELETE ステートメントの中にエラーが発生した場合に呼び出されるアップロードまたはダウンロードします。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> -DELETE ステートメントがされているときに呼び出されるアップロードまたはダウンロードします。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> のアップロードまたはダウンロード時に、INSERT ステートメントにエラーが発生した場合に呼び出されます。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> -INSERT ステートメントがされているときに呼び出されるアップロードまたはダウンロードします。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> -パブリッシャーとサブスクライバーで UPDATE ステートメントの競合が発生するときに呼び出されます。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> -UPDATE ステートメントがパブリッシャーとサブスクライバーの DELETE ステートメントと競合する場合に呼び出されます。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> のアップロードまたはダウンロード時に、UPDATE ステートメントにエラーが発生した場合に呼び出されます。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> -UPDATE ステートメントがされているときに呼び出されるアップロードまたはダウンロードします。  
  
    > [!NOTE]  
    >  アーティクル競合時の処理がカスタム ビジネス ロジックによって明示的に定義されていない場合は、アーティクルの既定の競合回避モジュールによって処理されます。  
  
6.  プロジェクトをビルドして、ビジネス ロジック ハンドラー アセンブリを作成します。  
  
#### ビジネス ロジック ハンドラーを登録するには  
  
1.  使用してディストリビューターへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.ReplicationServer> クラスです。 渡す、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 手順 1. のです。  
  
3.  呼び出す <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumBusinessLogicHandlers%2A> を確認して、返されたと <xref:System.Collections.ArrayList> アセンブリが既に登録されていないこと、ビジネス ロジック ハンドラーとしてことを確認するオブジェクト。  
  
4.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler> クラスです。 次のプロパティを指定します。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetAssemblyName%2A> -.NET アセンブリの名前。 マージ エージェントの実行可能ファイルがあるディレクトリ、マージ エージェントを同期的に起動するアプリケーションがあるディレクトリ、および GAC の、いずれとも異なる場所にアセンブリが配置されている場合は、アセンブリ名に完全パスを含める必要があります。 ビジネス ロジック ハンドラーを Web 同期で使用する場合は、アセンブリ名に完全パスを含める必要があります。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetClassName%2A> -オーバーライドするクラスの完全修飾名 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> し、ビジネス ロジック ハンドラーを実装します。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> -ビジネス ロジック ハンドラーにアクセスするときに使用する表示名。  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.IsDotNetAssembly%2A> -値の **true**します。  
  
#### ビジネス ロジック ハンドラーを配置するには  
  
1.  マージ エージェントが実行されるサーバーにアセンブリを配置します。格納場所は、ディストリビューターにビジネス ロジック ハンドラーを登録したときに指定した場所になります。 プル サブスクリプションの場合、エージェントはサブスクライバー上で実行されます。プッシュ サブスクリプションの場合、エージェントはディストリビューター上で実行されます。 Web 同期を使用した場合、エージェントは Web サーバー上で実行されます。 ビジネス ロジック ハンドラーの登録時、アセンブリ名に完全パスを含めなかった場合は、マージ エージェントの実行可能ファイルがあるディレクトリ (マージ エージェントを同期的に起動するアプリケーションがあるディレクトリ) にアセンブリを配置してください。 同じアセンブリを使用するアプリケーションが複数存在する場合は、アセンブリを GAC にインストールする必要があります。  
  
#### 新しいテーブル アーティクルでビジネス ロジック ハンドラーを使用するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergeArticle> クラスです。 次のプロパティを設定します。  
  
    -   アーティクルの名前 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>します。  
  
    -   パブリケーションの名前 <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>します。  
  
    -   パブリケーション データベースの名前 <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A>します。  
  
    -   ビジネス ロジック ハンドラーの表示名 (<xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A>) の <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>します。  
  
3.  呼び出す、 <xref:Microsoft.SqlServer.Replication.Article.Create%2A> メソッドです。 詳しくは、「 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
#### 既存のテーブル アーティクルでビジネス ロジック ハンドラーを使用するには  
  
1.  使用してパブリッシャーへの接続を作成、 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> クラスです。  
  
2.  インスタンスを作成、 <xref:Microsoft.SqlServer.Replication.MergeArticle> クラスです。  
  
3.  設定、 <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, 、<xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, 、および <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> プロパティです。  
  
4.  手順 1. の接続の設定、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> プロパティです。  
  
5.  呼び出す、 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> オブジェクトのプロパティを取得します。 このメソッドから **false**が返された場合、手順 3. で指定したアーティクルのプロパティが正しく定義されていないか、アーティクルが存在していません。 詳しくは、「 [View and Modify Article Properties](../../relational-databases/replication/publish/view-and-modify-article-properties.md)」をご覧ください。  
  
6.  ビジネス ロジック ハンドラーの表示名を設定 <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>します。 これは、値、 <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> ビジネス ロジック ハンドラーを登録するときに指定されたプロパティ。  
  
###  <a name="PShellExample"></a> 例 (RMO)  
 次のビジネス ロジック ハンドラーの例では、サブスクライバーでの挿入、更新、および削除に関する情報をログに記録します。  
  
 [!code-csharp[HowTo#rmo_BusinessLogicCode](../../relational-databases/replication/codesnippet/csharp/rmohowto/businesslogic.cs#rmo_businesslogiccode)]  
  
 [!code-vb[HowTo#rmo_vb_BusinessLogicCode](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/businesslogic.vb#rmo_vb_businesslogiccode)]  
  
 次の例では、ディストリビューターにビジネス ロジック ハンドラーを登録します。  
  
 [!code-csharp[HowTo#rmo_RegisterBLH_10](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_registerblh_10)]  
  
 [!code-vb[HowTo#rmo_vb_RegisterBLH_10](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_registerblh_10)]  
  
 次の例では、既存のアーティクルを変更してビジネス ロジック ハンドラーを使用します。  
  
 [!code-csharp[HowTo#rmo_ChangeMergeArticle_BLH](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changemergearticle_blh)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergeArticle_BLH](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changemergearticle_blh)]  
  
## 参照  
 [マージ アーティクルのカスタム競合回避モジュールの実装](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)   
 [#40; (&)、ビジネス ロジック ハンドラーをデバッグします。レプリケーション プログラミングと #41 です。](../../relational-databases/replication/debug-a-business-logic-handler-replication-programming.md)   
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [レプリケーション管理オブジェクトの概念](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)  
  
  