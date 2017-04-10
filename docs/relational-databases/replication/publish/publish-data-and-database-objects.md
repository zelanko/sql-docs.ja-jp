---
title: "データとデータベース オブジェクトのパブリッシュ | Microsoft Docs"
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
  - "ユーザー定義型 [SQL Server レプリケーション]"
  - "アーティクル [SQL Server レプリケーション]、ドロップ"
  - "オブジェクト [SQL Server レプリケーション]"
  - "パブリケーション [SQL Server レプリケーション]、作成"
  - "マージ レプリケーション [SQL Server レプリケーション], パブリケーション"
  - "スキーマだけのアーティクル [SQL Server レプリケーション]"
  - "パブリッシュ [SQL Server レプリケーション], データベース オブジェクト"
  - "アーティクル [SQL Server レプリケーション]、定義"
  - "パブリッシュ [SQL Server レプリケーション], 関数"
  - "レプリケーション [SQL Server レプリケーション], パブリケーション"
  - "パブリッシュ [SQL Server レプリケーション], ビュー"
  - "テーブル [SQL Server レプリケーション]"
  - "スキーマ [SQL Server レプリケーション]"
  - "パブリッシュ [SQL Server レプリケーション], データ"
  - "スキーマ [SQL Server レプリケーション], パブリッシュ"
  - "アーティクル [SQL Server レプリケーション], ストアド プロシージャと"
  - "パブリッシュ [SQL Server レプリケーション], テーブル"
  - "別名データ型 [SQL Server レプリケーション]"
  - "パブリケーション [SQL Server レプリケーション]、削除"
  - "スナップショット レプリケーション [SQL Server], パブリケーション"
  - "アーティクル [SQL Server レプリケーション]、変更"
  - "トランザクション レプリケーション, パブリケーション"
  - "パブリッシュ [SQL Server レプリケーション], ストアド プロシージャ"
  - "パブリッシング [SQL Server レプリケーション]"
  - "ビュー [SQL Server レプリケーション]"
  - "ストアド プロシージャ [SQL Server レプリケーション], パブリッシュ"
  - "パブリケーション [SQL Server レプリケーション], スキーマ オプション"
  - "アーティクル [SQL Server レプリケーション]、追加"
  - "パブリケーション [SQL Server レプリケーション]、変更"
  - "ユーザー定義関数 [SQL Server レプリケーション]"
ms.assetid: d986032c-3387-4de1-a435-3ec5e82185a2
caps.latest.revision: 83
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 83
---
# データとデータベース オブジェクトのパブリッシュ
  パブリケーションの作成時には、パブリッシュするテーブルやその他のデータベース オブジェクトを選択します。 レプリケーションを使用すると、以下のデータベース オブジェクトをパブリッシュできます。  
  
|データベース オブジェクト|スナップショット レプリケーションおよびトランザクション レプリケーション|マージ レプリケーション|  
|---------------------|--------------------------------------------------------|-----------------------|  
|テーブル|×|×|  
|パーティション テーブル|×|×|  
|ストアド プロシージャ - 定義 ([!INCLUDE[tsql](../../../includes/tsql-md.md)] および CLR)|×|×|  
|ストアド プロシージャ - 実行 ([!INCLUDE[tsql](../../../includes/tsql-md.md)] および CLR)|×|いいえ|  
|ビュー|×|×|  
|インデックス付きビュー|×|×|  
|テーブルとしてのインデックス付きビュー|×|いいえ|  
|ユーザー定義型 (CLR)|×|×|  
|ユーザー定義関数 ([!INCLUDE[tsql](../../../includes/tsql-md.md)] および CLR)|×|×|  
|別名データ型|×|×|  
|フルテキスト インデックス|×|×|  
|スキーマ オブジェクト (制約、インデックス、ユーザー DML トリガー、拡張プロパティ、および照合順序)|×|×|  
  
## パブリケーションの作成  
 パブリケーションを作成するには、次の情報を指定します。  
  
-   ディストリビューター。  
  
-   スナップショット ファイルの場所。  
  
-   パブリケーション データベース。  
  
-   作成するパブリケーションの種類 (スナップショット、トランザクション、更新可能なサブスクリプションを含むトランザクション、またはマージ)。  
  
-   パブリケーションに含めるデータとデータベース オブジェクト (アーティクル)。  
  
-   すべての種類のパブリケーションの静的行フィルターと列フィルター、およびマージ パブリケーションのパラメーター化された行フィルターと結合フィルター。  
  
-   スナップショット エージェントのスケジュール。  
  
-   エージェントの実行に使用するアカウント。対象となるエージェントは、スナップショット エージェント (すべてのパブリケーション用)、ログ リーダー エージェント (すべてのトランザクション パブリケーション用)、およびキュー リーダー エージェント (サブスクリプションの更新が許可されているトランザクション パブリケーション用) です。  
  
-   パブリケーションの名前と説明。  
  
 パブリケーションの操作方法の詳細については、次のトピックを参照してください。  
  
-   [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)  
  
-   [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)  
  
-   [パブリケーション プロパティの表示および変更](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)  
  
-   [アーティクルのプロパティの表示および変更](../../../relational-databases/replication/publish/view-and-modify-article-properties.md)  
  
-   [パブリケーションの削除](../../../relational-databases/replication/publish/delete-a-publication.md)  
  
-   [Delete an Article](../../../relational-databases/replication/publish/delete-an-article.md)  
  
> [!NOTE]  
>  アーティクルまたはパブリケーションを削除しても、オブジェクトはサブスクライバーから削除されません。  
  
## テーブルのパブリッシュ  
 パブリッシュされるオブジェクトで最も一般的なのはテーブルです。 以下のリンクは、テーブルのパブリッシュに関連する分野についての情報を提供します。  
  
-   [パブリッシュされたデータのフィルター選択](../../../relational-databases/replication/publish/filter-published-data.md)  
  
-   [トランザクション レプリケーションのアーティクル オプション](../../../relational-databases/replication/transactional/article-options-for-transactional-replication.md)  
  
-   [マージ レプリケーションのアーティクルのオプション](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)  
  
-   [ID 列のレプリケート](../../../relational-databases/replication/publish/replicate-identity-columns.md)  
  
 レプリケーションでテーブルをパブリッシュする場合、宣言された参照整合性 (主キー制約、参照に関する制約、一意制約)、インデックス、ユーザー DML トリガー (DDL トリガーはレプリケートできません)、拡張プロパティ、照合順序などの、サブスクライバーにコピーするスキーマ オブジェクトを指定できます。 拡張プロパティは、パブリッシャーとサブスクライバー間で初期同期を実行するときにのみレプリケートされます。 初期同期の完了後に拡張プロパティを追加または変更した場合、その変更はレプリケートされません。  
  
 スキーマ オプションを指定するを参照してください。 [スキーマ オプションの指定](../../../relational-databases/replication/publish/specify-schema-options.md) または <xref:Microsoft.SqlServer.Replication.Article.SchemaOption%2A>します。  
  
### パーティション テーブルとパーティション インデックス  
 レプリケーションでは、パーティション テーブルとパーティション インデックスのパブリッシュがサポートされます。 サポート レベルは、使用するレプリケーションの種類、パブリケーションに指定するオプション、およびパーティション テーブルに関連付けられたアーティクルによって異なります。 詳細については、次を参照してください。 [パーティション分割されたテーブルのレプリケートとインデックス](../../../relational-databases/replication/publish/replicate-partitioned-tables-and-indexes.md)します。  
  
## ストアド プロシージャのパブリッシュ  
 すべての種類のレプリケーションで、ストアド プロシージャの定義をレプリケートできます。各サブスクライバーに CREATE PROCEDURE がコピーされます。 共通言語ランタイム (CLR) ストアド プロシージャの場合は、関連するアセンブリもコピーされます。 プロシージャの変更はサブスクライバーにレプリケートされますが、関連するアセンブリの変更はレプリケートされません。  
  
 トランザクション レプリケーションでは、ストアド プロシージャの定義の他に、ストアド プロシージャの実行もレプリケートできます。 これは、大量のデータに影響を与えるメンテナンス用ストアド プロシージャの結果をレプリケートする場合に便利です。 詳細については、「 [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md)」を参照してください。  
  
## ビューのパブリッシュ  
 すべての種類のレプリケーションで、ビューをレプリケートできます。 ビュー (インデックス付きビューの場合は付属するインデックスも含む) はサブスクライバーにコピーできますが、ベース テーブルもレプリケートする必要があります。  
  
 トランザクション レプリケーションでは、インデックス付きビューをビューではなくテーブルとしてレプリケートできます。この場合、ベース テーブルをレプリケートする必要はありません。 これを行うには、"indexed view logbased"オプションのいずれかの指定、 *@type* のパラメーター [sp_addarticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)します。 使用の詳細については **sp_addarticle**, を参照してください [アーティクルを定義](../../../relational-databases/replication/publish/define-an-article.md)します。  
  
## ユーザー定義関数のパブリッシュ  
 CLR 関数および [!INCLUDE[tsql](../../../includes/tsql-md.md)] 関数の CREATE FUNCTION ステートメントが各サブスクライバーにコピーされます。 CLR 関数の場合は、関連するアセンブリもコピーされます。 関数の変更はサブスクライバーにレプリケートされますが、関連するアセンブリの変更はレプリケートされません。  
  
## ユーザー定義型および別名データ型のパブリッシュ  
 ユーザー定義型または別名データ型を使用する列は、他の列と同様にサブスクライバーにレプリケートされます。 テーブルが作成される前に、レプリケートされた種類ごとに作成 TYPEstatement はサブスクライバーで実行します。 ユーザー定義型の場合は、関連するアセンブリも各サブスクライバーにコピーされます。 ユーザー定義型および別名データ型の変更はサブスクライバーにレプリケートされません。  
  
 データベースで型が定義されている場合でも、パブリケーションの作成時に列で参照されていなければ、その型はサブスクライバーにコピーされません。 この型を使用する列を後でデータベースに作成してレプリケートする場合、最初にこの型 (ユーザー定義型の場合は関連するアセンブリも含む) を手動で各サブスクライバーにコピーする必要があります。  
  
## フルテキスト インデックスのパブリッシュ  
 CREATE FULLTEXT INDEX ステートメントが各サブスクライバーにコピーされ、フルテキスト インデックスがサブスクライバーに作成されます。 ALTER FULLTEXT INDEX を使用して行われたフルテキスト インデックスの変更はレプリケートされません。  
  
## パブリッシュされたオブジェクトに対するスキーマの変更  
 レプリケーションは、パブリッシュされたオブジェクトに対するさまざまなスキーマ変更をサポートしています。 パブリッシュされた適切なオブジェクトに対して、以下に示すスキーマ変更を [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] パブリッシャーで実行した場合、既定ではすべての [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サブスクライバーにその変更が反映されます。  
  
-   ALTER TABLE  
  
-   ALTER VIEW  
  
-   ALTER PROCEDURE  
  
-   ALTER FUNCTION  
  
-   ALTER TRIGGER  
  
 詳細については、次を参照してください。 [パブリケーション データベースでスキーマ変更を行う](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)します。  
  
## パブリッシングに関する注意点  
 データベース オブジェクトをパブリッシュするときは、以下の点に注意してください。  
  
-   パブリケーションおよび初期スナップショットの作成中でもユーザーはデータベースにアクセスできますが、パブリッシャーの利用状況が低い時間帯にパブリケーションを作成することをお勧めします。  
  
-   データベースにパブリケーションを作成した後で、そのデータベースの名前を変更することはできません。 データベース名を変更するには、まずデータベースからレプリケーションを削除する必要があります。  
  
-   1 つまたは複数の他のデータベース オブジェクトに依存するデータベース オブジェクトをパブリッシュする場合、参照されているオブジェクトをすべてパブリッシュする必要があります。 たとえば、テーブルに依存しているビューをパブリッシュする場合は、そのテーブルもパブリッシュする必要があります。  
  
    > [!NOTE]  
    >  マージ パブリケーションにアーティクルを追加すると、既存のアーティクルは、新しいアーティクルによって異なります。、、を使用して両方のアーティクルの処理順序を指定する必要があります、 **@processing_order** のパラメーター [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) と [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)します。 たとえば、テーブルをパブリッシュし、テーブルが参照している関数はパブリッシュしない場合を考えます。 この関数をパブリッシュしないと、サブスクライバー側でテーブルを作成できないとします。 パブリケーションに関数を追加すると: の値を指定して **1** の **@processing_order** のパラメーター **sp_addmergearticle**; の値を指定 **2** の **@processing_order** のパラメーター **sp_changemergearticle**, 、テーブル名、パラメーターを指定する **@article**します。 この処理順序により、サブスクライバー側で関数に依存するテーブルを作成する前に、関数の作成が求められるようになります。 各アーティクルに使用する値は、関数の値がテーブルの値より小さければ、別の値でもかまいません。  
  
-   パブリケーション名には、% * [ ] | : " ? を使用できません。 \ / \< >.  
  
### オブジェクトのパブリッシュに関する制限事項  
  
-   パブリッシュできるアーティクルおよび列の最大数は、パブリケーションの種類によって異なります。 詳細については、の「レプリケーション オブジェクト」セクションを参照してください。 [SQL Server の最大容量仕様](../../../sql-server/maximum-capacity-specifications-for-sql-server.md)します。  
  
-   WITH ENCRYPTION として定義されているストアド プロシージャ、ビュー、トリガー、およびユーザー定義関数は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーションの一部としてパブリッシュすることはできません。  
  
-   XML スキーマ コレクションはレプリケートできますが、初期スナップショットの後で変更をレプリケートすることはできません。  
  
-   トランザクション レプリケーションでは、パブリッシュされたテーブルは主キーを持たなければなりません。 テーブルがトランザクション レプリケーション パブリケーション内にある場合、主キー列に関連付けられているインデックスを無効にすることはできません。 これらのインデックスはレプリケーションで必要です。 インデックスを無効にするには、まずパブリケーションからテーブルを削除する必要があります。  
  
-   作成されたデフォルトをバインド [sp_bindefault & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md) レプリケートされません (バインドされた既定値は ALTER TABLE または CREATE TABLE の DEFAULT キーワードで作成されたデフォルトを優先して非推奨)。  
  
-   関数を含む、 **NOEXPAND** インデックス付きビューのヒントにことはできません、ディストリビューション エージェントがそれらに配信順序を原因として参照されているテーブルおよびインデックス付きビューは、同じパブリケーションでパブリッシュします。 この問題を解決するには、最初のパブリケーションのテーブルおよびインデックス付きビューの作成を配置しを含む関数を追加、 **NOEXPAND** 後、最初のパブリケーションにパブリッシュする 2 番目のドキュメントをインデックス付きビューにヒントが完了するとします。 または、これらの関数のスクリプトを作成しを使用して、スクリプトを配信、 *@post_snapshot_script* のパラメーター **sp_addpublication**します。  
  
### スキーマおよびオブジェクトの所有権  
 既定では、パブリケーションの新規作成ウィザードは、スキーマとオブジェクトの所有権に関して、以下のように動作します。  
  
-   互換性レベル 90 以上のマージ パブリケーションと、スナップショット パブリケーション、およびトランザクション パブリケーションのアーティクルの場合、既定では、サブスクライバーでのオブジェクト所有者は、パブリッシャーでの対応するオブジェクトの所有者と同じになります。 オブジェクトを所有するスキーマがサブスクライバーに存在しない場合は、スキーマが自動的に作成されます。  
  
-   互換性レベルが 90 未満のマージ パブリケーションのアーティクルの: 既定では、所有者は空白のままし、として指定された **dbo** サブスクライバー上のオブジェクトの作成時にします。  
  
-   Oracle パブリケーションのアーティクル: として既定では、所有者が指定されている **dbo**します。  
  
-   キャラクター モードのスナップショット ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のバージョンのサブスクライバーや [!INCLUDE[ssEW](../../../includes/ssew-md.md)] サブスクライバーで使用されます) を使用するパブリケーションのアーティクルの場合。既定では、所有者は空白のままになります。 既定の所有者は、サブスクライバーに接続しているディストリビューション エージェントまたはマージ エージェントで使用されるアカウントに関連付けられている所有者になります。  
  
 を介して、オブジェクトの所有者を変更すること、 **アーティクルのプロパティ - \<***記事***>** ] ダイアログ ボックスおよびストアド プロシージャは次の手順: **sp_addarticle**, 、**sp_addmergearticle**, 、**sp_changearticle**, 、および **sp_changemergearticle**します。 詳細については、次を参照してください。 [パブリケーション プロパティの変更を表示および](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md), 、[アーティクルを定義](../../../relational-databases/replication/publish/define-an-article.md), 、および [アーティクル プロパティの変更を表示および](../../../relational-databases/replication/publish/view-and-modify-article-properties.md)です。  
  
### 以前のバージョンの SQL Server を実行するサブスクライバーへのデータのパブリッシュ  
  
-   以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を実行するサブスクライバーにパブリッシュする場合、レプリケーション固有の機能および製品の全般的な機能は共に、該当するバージョンの機能に制限されます。  
  
-   マージ パブリケーションでは互換性レベルが利用されます。この互換性レベルによってパブリケーションで使用する機能が決定され、また以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を実行するサブスクライバーをサポートできるようになります。  
  
### 複数のパブリケーションでのテーブルのパブリッシュ  
 レプリケーションでは、以下に示す制限付きで、アーティクルを複数のパブリケーションでパブリッシュできます (データの再パブリッシュを含む)。  
  
-   場合は、トランザクション パブリケーションおよびマージ パブリケーションでアーティクルをパブリッシュすると、確認、 *@published_in_tran_pub* マージ アーティクルのプロパティが TRUE に設定します。 プロパティの設定の詳細については、次を参照してください。 [パブリケーション プロパティの変更を表示および](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md) と [アーティクル プロパティの変更を表示および](../../../relational-databases/replication/publish/view-and-modify-article-properties.md)です。  
  
     設定する必要がありますも、 *@published_in_tran_pub* アーティクルはトランザクション パブリケーションに対するサブスクリプションの一部であり、マージ パブリケーションに含まれる場合はプロパティです。 これに該当する場合、特に指定がなければ、トランザクション レプリケーションでは、サブスクライバー側のテーブルが読み取り専用として扱われるものと想定しているので、注意が必要です。マージ レプリケーションがトランザクション サブスクリプションに含まれるテーブルに対してデータ変更を行うと、データの非収束が発生する可能性があります。 この可能性を回避するため、マージ パブリケーションではこのようなテーブルをダウンロードのみとして指定することをお勧めします。 これはマージ サブスクライバーがテーブルにデータの変更をアップロードすることを防ぎます。 詳細については、次を参照してください。 [Download-Only アーティクルを使用したマージ レプリケーション パフォーマンスの最適化](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md)します。  
  
-   マージ パブリケーションおよびキュー更新サブスクリプションを使用するトランザクション パブリケーションのどちらも、アーティクルをパブリッシュすることはできません。  
  
-   更新サブスクリプションをサポートするトランザクション パブリケーションのアーティクルを再パブリッシュすることはできません。  
  
-   キュー更新サブスクリプションをサポートする複数のトランザクション パブリケーションでアーティクルをパブリッシュする場合には、すべてのパブリケーションで、次に示すプロパティの値を同一にする必要があります。  
  
    |プロパティ|sp_addarticle のパラメーター|  
    |--------------|---------------------------------|  
    |ID 範囲の管理|**@auto_identity_range** (非推奨) と **@identityrangemangementoption**|  
    |パブリッシャーの ID 範囲|**@pub_identity_range**|  
    |ID 範囲|**@identity_range**|  
    |ID 範囲のしきい値|**@threshold**|  
  
     これらのパラメーターの詳細については、次を参照してください。 [sp_addarticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)します。  
  
-   複数のマージ パブリケーションでアーティクルをパブリッシュする場合には、すべてのパブリケーションにわたって、以下に示すプロパティの値を同一にする必要があります。  
  
    |プロパティ|sp_addmergearticle のパラメーター|  
    |--------------|--------------------------------------|  
    |列追跡|**@column_tracking**|  
    |スキーマ オプション|**@schema_option**|  
    |列のフィルター選択|**@vertical_partition**|  
    |サブスクライバーのアップロード オプション|**@subscriber_upload_options**|  
    |条件付き削除の追跡|**@delete_tracking**|  
    |エラー補正|**@compensate_for_errors**|  
    |ID 範囲の管理|**@auto_identity_range** (非推奨) と **@identityrangemangementoption**|  
    |パブリッシャーの ID 範囲|**@pub_identity_range**|  
    |ID 範囲|**@identity_range**|  
    |ID 範囲のしきい値|**@threshold**|  
    |[パーティションのオプション]|**@partition_options**|  
    |BLOB 列のストリーミング|**@stream_blob_columns**|  
    |フィルターの種類|**@filter_type** (パラメーター **sp_addmergefilter**)|  
  
     これらのパラメーターの詳細については、次を参照してください。 [sp_addmergearticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)  [sp_addmergefilter & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)します。  
  
-   トランザクション レプリケーションおよびフィルター選択されていないマージ レプリケーションでは、複数のパブリケーションでのテーブルのパブリッシュを行ってから、サブスクリプション データベースの単一テーブル内でサブスクライブすることがサポートされています (一般にロール アップ シナリオと呼ばれています)。 ロール アップは、複数の場所からのデータを中央のサブスクライバーの単一テーブルに集計することを目的として使用されるのが一般的です。 フィルター選択されたマージ パブリケーションでは、中央のサブスクライバーを使用するシナリオはサポートされません。 マージ レプリケーションでは通常、パラメーター化された行フィルターを使用した単一のパブリケーションを介してロール アップが実装されます。 詳しくは、「 [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md)」をご覧ください。  
  
## 参照  
 [既存のパブリケーションでのアーティクルの追加および削除](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)   
 [ディストリビューションの構成](../../../relational-databases/replication/configure-distribution.md)   
 [サブスクリプションの初期化](../../../relational-databases/replication/initialize-a-subscription.md)   
 [レプリケーションのスクリプト作成](../../../relational-databases/replication/scripting-replication.md)   
 [パブリッシャーのセキュリティ保護](../../../relational-databases/replication/security/secure-the-publisher.md)   
 [パブリケーションのサブスクライブ](../../../relational-databases/replication/subscribe-to-publications.md)  
  
  