---
title: "マージ アーティクル競合回避モジュールの指定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アーティクル [SQL Server レプリケーション], 競合回避"
  - "競合回避 [SQL Server レプリケーション], マージ レプリケーション"
  - "マージ レプリケーションの競合回避 [SQL Server レプリケーション], マージ アーティクル競合回避"
ms.assetid: a40083b3-4f7b-4a25-a5a3-6ef67bdff440
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# マージ アーティクル競合回避モジュールの指定
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、マージ アーティクル競合回避モジュールを指定する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [推奨事項](#Recommendations)  
  
-   **マージ アーティクル競合回避モジュールを指定するために使用するもの:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   マージ レプリケーションでは、以下の競合回避モジュールが使用できます。  
  
    -   既定の競合回避モジュール。 既定の競合回避モジュールの動作は、サブスクリプションがクライアント サブスクリプションまたはサーバー サブスクリプションのどちらであるかによって異なります。 サブスクリプションの種類を指定する方法の詳細については、次を参照してください。 [指定マージ サブスクリプションの種類と競合解決の優先度と #40 です。SQL Server Management Studio と #41;](../../../relational-databases/replication/specify a merge subscription type and conflict resolution priority.md)します。  
  
    -   ユーザーの作成したカスタム競合回避モジュール。ビジネス ロジック ハンドラー (マネージ コードで作成) または COM ベースのカスタム競合回避モジュールです。 詳細については、「 [Advanced Merge Replication Conflict Detection and Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)」を参照してください。 参照してください、競合する行に対してだけでなく、レプリケートされた行ごとに実行されるカスタム ロジックを実装する必要がある場合 [マージ アーティクルのビジネス ロジック ハンドラーを実装](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)します。  
  
    -   標準的な COM ベース競合回避モジュールに含まれている [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。  
  
-   既定以外の競合回避モジュールを使用する場合は、マージ エージェントが動作しているコンピューターにそのモジュールをコピーして登録する必要があります (ビジネス ロジック ハンドラーを使用している場合は、そのビジネス ロジック ハンドラーもパブリッシャー側で登録する必要があります)。 マージ エージェントは、以下の場所で実行されます。  
  
    -   プッシュ サブスクリプションの場合はディストリビューター  
  
    -   プル サブスクリプションの場合はサブスクライバー  
  
    -   Web 同期を使用するプル サブスクリプションの場合は [!INCLUDE[msCoName](../../../includes/msconame-md.md)] インターネット インフォメーション サービス (IIS) サーバー  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
 競合回避モジュールが登録された後にアーティクルが、競合回避モジュールを使用することを指定、 **リゾルバー** のタブ、 **アーティクルのプロパティ - \< 記事>** パブリケーションの新規作成ウィザードで使用可能なダイアログ ボックスおよび **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックス。 ウィザードを使用して、ダイアログ ボックスへのアクセスに関する詳細については、次を参照してください。 [パブリケーションを作成](../../../relational-databases/replication/publish/create-a-publication.md) と [パブリケーション プロパティの変更を表示および](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)です。  
  
#### 競合回避モジュールを指定するには  
  
1.   **記事** パブリケーションの新規作成ウィザードのページまたは **パブリケーションのプロパティ - \< パブリケーション>** ] ダイアログ ボックスでテーブルを選択します。  
  
2.  **[アーティクルのプロパティ]**をクリックしてから、 **[反転表示されたテーブル アーティクルのプロパティを設定]**をクリックします。  
  
3.   **アーティクルのプロパティ - \< 記事>** ] ページで、をクリックして、 **リゾルバー** ] タブをクリックします。  
  
4.  選択 **(ディストリビューターで登録されている) のカスタム競合回避モジュールを使用して**, 、ボックスの一覧で、競合回避モジュールをクリックします。  
  
5.  競合回避モジュールは、(列名) などの入力を必要とする場合は指定で、 **、競合回避モジュールに必要な情報を入力** テキスト ボックスです。  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
7.  競合回避モジュールを必要とする各アーティクルについて、この処理を繰り返します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### カスタム競合回避モジュールを登録するには  
  
1.  固有のカスタム競合回避モジュールを登録する場合は、次のいずれかの種類を作成します。  
  
    -   ビジネス ロジック ハンドラーとしてのマネージ コード ベースの競合回避モジュール。 詳しくは、「 [Implement a Business Logic Handler for a Merge Article](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)」をご覧ください。  
  
    -   ストアド プロシージャ ベースの競合回避モジュールと COM-ベースの競合回避モジュール。 詳しくは、「 [Implement a Custom Conflict Resolver for a Merge Article](../../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)」をご覧ください。  
  
2.  目的の競合回避モジュールが既に登録されているかどうかを確認するのには、実行 [sp_enumcustomresolvers & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) パブリッシャーのデータベースに対して。 これにより、カスタム競合回避モジュールの説明、およびディストリビューターに登録された各 COM ベースの競合回避モジュールのクラス識別子 (LSID)、またはディストリビューターに登録された各ビジネス ロジック ハンドラーのマネージ アセンブリの情報が表示されます。  
  
3.  目的のカスタム競合回避モジュールが登録されていない場合、実行 [sp_registercustomresolver & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md) ディストリビューターです。 競合回避モジュールの名前を指定 **@article_resolver**; ビジネス ロジック ハンドラー アセンブリのフレンドリ名です。 COM ベース競合回避モジュールの DLL の CLSID を指定する **@resolver_clsid**, 、ビジネス ロジック ハンドラーの値を指定して **true** の **@is_dotnet_assembly**, のアセンブリの名前 **@dotnet_assembly_name**, 、およびオーバーライドするクラスの完全修飾名 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> の **@dotnet_class_name**します。  
  
    > [!NOTE]  
    >  ビジネス ロジック ハンドラー アセンブリが配置されているマージ エージェント実行可能ファイルと同じディレクトリ、アプリケーションと同じディレクトリを同期的に起動、マージ エージェント、または、グローバル アセンブリ キャッシュ (GAC) 内のアセンブリ名を持つ完全なパスを指定する必要があります。 場合 **@dotnet_assembly_name**します。  
  
4.  競合回避モジュールが COM ベースの場合  
  
    -   カスタム競合回避モジュール DLL をプッシュ サブスクリプションのディストリビューター、またはプル サブスクリプションのサブスクライバーにコピーします。  
  
        > [!NOTE]  
        >  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] カスタム競合回避モジュールを参照して、 [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM ディレクトリ。  
  
    -   regsvr32.exe を使用して、カスタム競合回避モジュール DLL をオペレーティング システムに登録します。 たとえば、次のコマンドをコマンド プロンプトから実行すると、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Additive Conflict Resolver が登録されます。  
  
        ```  
        regsvr32 ssradd.dll  
        ```  
  
5.  競合回避モジュールがビジネス ロジック ハンドラーの場合は、または指定したフォルダーに、マージ エージェントを起動するアプリケーションと同じフォルダーにマージ エージェント実行可能ファイル (replmerg.exe) と同じフォルダーにアセンブリを配置、 **@dotnet_assembly_name** 手順 3 でのパラメーターです。  
  
    > [!NOTE]  
    >  マージ エージェント実行可能ファイルの既定のインストール場所は、[!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM です。  
  
#### マージ アーティクルを定義するときにカスタム競合回避モジュールを指定するには  
  
1.  カスタム競合回避モジュールを使用する場合は、上記の手順に従って競合回避モジュールを作成および登録します。  
  
2.  パブリッシャーで実行 [sp_enumcustomresolvers & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) 目的のカスタム競合回避モジュールの名前をメモして、 **値** 結果セットのフィールドです。  
  
3.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergearticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)します。 手順 2. の競合回避モジュールの名前を指定 **@article_resolver** 必要なすべての入力を使用してカスタム競合回避モジュールを **@resolver_info** パラメーター。 ストアド プロシージャ ベース カスタム競合回避モジュールの **@resolver_info** ストアド プロシージャの名前を指定します。 によって提供される競合回避モジュールに必要な情報の詳細については [!INCLUDE[msCoName](../../../includes/msconame-md.md)], を参照してください [Microsoft COM ベース競合回避モジュール](../../../relational-databases/replication/merge/microsoft-com-based-resolvers.md)します。  
  
#### 既存のマージ アーティクルに対するカスタム競合回避モジュールを指定または変更するには  
  
1.  カスタム競合回避モジュールが、アーティクルに対して定義されているかどうかを判断するか、競合回避モジュールの名前を取得するには、実行 [sp_helpmergearticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)します。 その名前が表示されるアーティクルの定義のカスタム競合回避モジュールがある場合、 **article_resolver** フィールドです。 表示される競合回避モジュールをすべての入力、 **resolver_info** 結果セットのフィールドです。  
  
2.  パブリッシャーで実行 [sp_enumcustomresolvers & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) 目的のカスタム競合回避モジュールの名前をメモして、 **値** 結果セットのフィールドです。  
  
3.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_changemergearticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)します。 値を指定して **article_resolver**, のビジネス ロジック ハンドラーの完全パスを含む **@property**, 、手順 2. の目的のカスタム競合回避モジュールの名前と **@value**します。  
  
4.  カスタム競合回避モジュールの必須入力を変更するには、実行 [sp_changemergearticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) もう一度です。 値を指定して **resolver_info** の **@property** 、必須のカスタム競合回避モジュールへの入力 **@value**します。 ストアド プロシージャ ベース カスタム競合回避モジュールの **@resolver_info** ストアド プロシージャの名前を指定します。 必要な入力の詳細については、次を参照してください。 [Microsoft COM ベース競合回避モジュール](../../../relational-databases/replication/merge/microsoft-com-based-resolvers.md)します。  
  
#### カスタム競合回避モジュールの登録を解除するには  
  
1.  パブリッシャーで実行 [sp_enumcustomresolvers & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) 削除するカスタム競合回避モジュールの名前をメモして、 **値** 結果セットのフィールドです。  
  
2.  実行 [sp_unregistercustomresolver & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md) ディストリビューターです。 手順 1. のカスタム競合回避モジュールの完全な名前を指定 **@article_resolver**します。  
  
###  <a name="TsqlExample"></a> 例 (Transact-SQL)  
 次の例では、新しいアーティクルを作成し、競合が発生したときに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] UnitPrice **列の平均の計算に** Averaging Conflict Resolver が使用されるように指定します。  
  
 [!code-sql[HowTo#sp_addmerge_resolver](../../../relational-databases/replication/codesnippet/tsql/specify-a-merge-article-_1.sql)]  
  
 次の例では、アーティクルを変更して、競合が発生したときに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] UnitsOnOrder **列の合計の計算に** Additive Conflict Resolver が使用されるように指定します。  
  
 [!code-sql[HowTo#sp_changemerge_resolver](../../../relational-databases/replication/codesnippet/tsql/specify-a-merge-article-_2.sql)]  
  
## 参照  
 [マージ レプリケーションの競合検出および解決の詳細](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [マージ アーティクルのビジネス ロジック ハンドラーの実装](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)  
  
  