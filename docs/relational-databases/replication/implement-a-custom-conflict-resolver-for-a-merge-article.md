---
title: "マージ アーティクルのカスタム競合回避モジュールの実装 | Microsoft Docs"
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
  - "マージ レプリケーションの競合解決 [SQL Server レプリケーション], ストアド プロシージャ ベースの競合回避モジュール"
  - "アーティクル [SQL Server レプリケーション], 競合解決"
  - "競合回避 [SQL Server レプリケーション]、マージ レプリケーション"
ms.assetid: 76bd8524-ebc1-4d80-b5a2-4169944d6ac0
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# マージ アーティクルのカスタム競合回避モジュールの実装
  このトピックで、マージ アーティクルのカスタム競合回避モジュールを実装する方法について説明 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] または [COM ベース カスタム競合回避モジュール](../../relational-databases/replication/merge/com-based-custom-resolvers.md)します。  
  
 **このトピックの内容**  
  
-   **マージ アーティクルのカスタム競合回避モジュールを実装するためにに使用するもの:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [COM ベースの競合回避モジュール](#COM)  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
 各パブリッシャーで、固有のカスタム競合回避モジュールを [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャとして記述できます。 同期中に、このストアド プロシージャは、競合回避モジュールが登録されているアーティクル内で競合が発生した場合に呼び出されます。競合する行の情報は、マージ エージェントによってプロシージャの必須パラメーターに渡されます。 ストアド プロシージャ ベースのカスタム競合回避モジュールは、常にパブリッシャーで作成されます。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャ競合回避モジュールは、行の変更ベースの競合を処理するのみ呼び出されます。 このモジュールは、他の種類の競合 (PRIMARY KEY 違反による挿入の失敗や一意インデックス制約違反) の処理には使用できません。  
  
#### ストアド プロシージャ ベースのカスタム競合回避モジュールを作成するには  
  
1.  パブリッシャーのパブリケーションまたは **msdb** データベースで、次の必須パラメーターを実装する新しいシステム ストアド プロシージャを作成します。  
  
    |パラメーター|データ型|説明|  
    |---------------|---------------|-----------------|  
    |**@tableowner**|**sysname**|競合を解決する対象のテーブルの所有者名。 これは、パブリケーション データベース内のテーブルの所有者です。|  
    |**@tablename**|**sysname**|競合を解決する対象のテーブル名。|  
    |**@rowguid**|**uniqueidentifier**|競合している行の一意の識別子。|  
    |**@subscriber**|**sysname**|競合する変更の反映元であるサーバーの名前。|  
    |**@subscriber_db**|**sysname**|競合する変更の反映元であるデータベースの名前。|  
    |**@log_conflict OUTPUT**|**int**|競合を後で解決できるように、マージ処理で競合をログに記録するかどうかを指定します。<br /><br /> **0** = は、競合ログに記録されません。<br /><br /> **1** = サブスクライバーは競合で優先されません。<br /><br /> **2** = パブリッシャーは競合で優先されません。|  
    |**@conflict_message OUTPUT**|**nvarchar (512)**|競合をログに記録する場合の解決に関するメッセージ。|  
    |**@destowner**|**sysname**|サブスクライバー側でパブリッシュされたテーブルの所有者。|  
  
     このストアド プロシージャは、マージ エージェントからパラメーターに渡された値を使用して、カスタム競合回避ロジックを実装します。このロジックでは、ベース テーブルと同じ構造を持ち、競合で優先されたバージョンの行のデータ値を含んでいる、単一行の結果セットを返す必要があります。  
  
2.  サブスクライバーでパブリッシャーへの接続に使用される任意のログインに対して、ストアド プロシージャの EXECUTE 権限を許可します。  
  
#### 新しいテーブル アーティクルにカスタム競合回避モジュールを使用するには  
  
1.  実行 [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) の値を指定するアーティクルを定義する **MicrosoftSQL** **サーバー ストアド プロシージャのリゾルバー** の **@article_resolver** パラメーターとの競合回避ロジックを実装するストアド プロシージャの名前、 **@resolver_info** パラメーター。 詳しくは、「 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
#### 既存のテーブル アーティクルにカスタム競合回避モジュールを使用するには  
  
1.  実行 [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), を指定して、 **@publication**, 、**@article**, の値 **article_resolver** の **@property**, の値との **MicrosoftSQL** **Server 格納 ProcedureResolver** の **@value**します。  
  
2.  実行 [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), を指定して **@publication**, 、**@article**, の値 **resolver_info** の **@property**, 、競合回避ロジックを実装するストアド プロシージャの名前と **@value**します。  
  
##  <a name="COM"></a> COM ベースのカスタム競合回避モジュールの使用  
  <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> 名前空間は、イベントを処理し、マージ レプリケーションの同期処理中に発生する競合を解決するには複雑なビジネス ロジックを記述することができますインターフェイスを実装します。 詳しくは、「 [Implement a Business Logic Handler for a Merge Article](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)」をご覧ください。 また、ネイティブ コード ベースのカスタム ビジネス ロジックを独自に作成して、競合を回避することもできます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C++ などの製品を使用して、このロジックを COM コンポーネントとしてビルドし、ダイナミック リンク ライブラリ (DLL) にコンパイルします。 このような COM ベース カスタム競合回避モジュールを実装する必要があります、 **ICustomResolver** 競合解決専用に設計されたインターフェイスです。  
  
#### COM ベース カスタム競合回避モジュールを作成して登録するには  
  
1.  COM 互換のオーサリング環境で、カスタム競合回避モジュール ライブラリへの参照を追加します。  
  
2.  Visual C++ プロジェクトの場合は、#import ディレクティブを使用してこのライブラリをプロジェクトにインポートします。  
  
3.  **ICustomResolver** インターフェイスを実装するクラスを作成します。  
  
4.  メソッドとプロパティを実装します。  
  
5.  プロジェクトをビルドして、カスタム競合回避モジュール ライブラリ ファイルを作成します。  
  
6.  マージ エージェントの実行可能ファイルが置かれているディレクトリ (通常は \Microsoft SQL Server\100\COM) に、そのライブラリを配置します。  
  
    > [!NOTE]  
    >  カスタム競合回避モジュールは、プル サブスクリプションの場合はサブスクライバーに、プッシュ サブスクリプションの場合はディストリビューターに、Web 同期に使用する場合は Web サーバーに配置する必要があります。  
  
7.  次のように、配置先のディレクトリから regsvr32.exe を使用してカスタム競合回避モジュール ライブラリを登録します。  
  
    ```  
    regsvr32.exe mycustomresolver.dll  
    ```  
  
8.  パブリッシャーで実行 [sp_enumcustomresolvers & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) ライブラリが既にはカスタム競合回避モジュールとして登録いないことを確認します。  
  
9. カスタム競合回避モジュールとして、ライブラリを登録するには、実行 [sp_registercustomresolver & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md), 、ディストリビューターでします。 COM オブジェクトのフレンドリ名を指定 **@article_resolver**, のライブラリの ID (CLSID) **@resolver_clsid**, の値との **false** の **@is_dotnet_assembly**します。  
  
    > [!NOTE]  
    >  カスタム競合回避モジュールを使用して登録できます必要なくなったときに [sp_unregistercustomresolver & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md)します。  
  
10. (省略可) クラスターで手順 5. ～ 8. を繰り返して、クラスターの全ノードにカスタム競合回避モジュールを登録します。 この手順は、フェールオーバーの後にカスタム競合回避モジュールに調整エージェントを適切に読み込むために必要です。  
  
#### 新しいテーブル アーティクルにカスタム競合回避モジュールを使用するには  
  
1.  パブリッシャーで実行 [sp_enumcustomresolvers & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) 目的の競合回避モジュールの表示名をメモしておきます。  
  
2.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergearticle & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) アーティクルを定義します。 手順 1. のアーティクル競合回避モジュールのフレンドリ名を指定して **@article_resolver**します。 詳しくは、「 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
#### 既存のテーブル アーティクルにカスタム競合回避モジュールを使用するには  
  
1.  パブリッシャーで実行 [sp_enumcustomresolvers & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) 目的の競合回避モジュールの表示名をメモしておきます。  
  
2.  実行 [sp_changemergearticle & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), を指定して **@publication**, 、**@article**, の値 **article_resolver** の **@property**, 、手順 1. のアーティクル競合回避モジュールの表示名と **@value**します。  
  
#### サンプルのカスタム競合回避モジュールの表示  
  
1.  SQL Server 2000 サンプル ファイルにサンプルが提供されています。 「 **SQL Server 2000 Service Pack 3 用の更新されたサンプル** 」から [sql2000samples.cab](http://www.microsoft.com/download/details.aspx?id=8560)をダウンロードします。 これによって、合計 6.9 MB の 8 つのファイルがダウンロードされます。  
  
2.  ダウンロードされた圧縮済み .cab ファイルからファイルを抽出します。  
  
3.   **setup.exe**を実行します。  
  
    > [!NOTE]  
    >  インストール オプションを選択する場合は、 **レプリケーション** サンプルをインストールするだけで済みます。 (既定のインストール パスは **C:\Program ファイル (x86) \Microsoft SQL Server 2000 Samples\1033\\**)  
  
4.  インストール フォルダーに移動します。 (既定のフォルダーは **C:\Program ファイル (x86) \Microsoft SQL Server 2000 Samples\1033\sqlrepl\unzip_sqlreplSP3.exe**)  
  
5.  実行、 **unzip_sqlreplSP3.exe** プログラムです。  
  
    > [!NOTE]  
    >  サンプルの com 競合回避モジュールがインストール (既定)、 **C:\Program Files (x86) \Microsoft SQL Server 2000 Samples\1033\sqlrepl\resolver\subspres** フォルダーです。  
  
6.   **Subspres** フォルダーの出現箇所をすべて検索 **#include sqlres.h** ソース ファイルのすべての行で置き換えます **#import"replrec.dll"no_namespace、raw_interfaces_only**  
  
## 参照  
 [マージ レプリケーションの競合検出および解決の詳細](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [COM ベースのカスタム競合回避モジュール](../../relational-databases/replication/merge/com-based-custom-resolvers.md)   
 [レプリケーション セキュリティの推奨事項](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  