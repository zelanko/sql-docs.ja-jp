---
title: "[パブリケーションのプロパティ]、[サブスクリプション オプション] | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.pubproperties.subscriptionoptions.f1"
ms.assetid: 31abd605-b273-419d-86df-d0ecf539a507
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# [パブリケーションのプロパティ]、[サブスクリプション オプション]
   **サブスクリプション オプション** のページ、 **パブリケーションのプロパティ** ダイアログ ボックスでは、表示し、パブリケーションのサブスクリプションに関連付けられているレベルのプロパティを設定することができます。 プロパティは次のように分類されます。  
  
-   すべてのパブリケーションに適用されるプロパティ。  
  
-   スナップショット パブリケーションおよびトランザクション パブリケーション (サブスクリプションの更新を許可するパブリケーションを含む) に適用されるプロパティ。  
  
-   マージ パブリケーションに適用されるプロパティ。  
  
> [!NOTE]  
>  一部のプロパティは読み取り専用です。理由については、このトピックのプロパティの解説で説明します。 プロパティの変更に応じて、新しいスナップショットが必要になる場合や、すべてのサブスクリプションの再初期化が必要になる場合があります。 詳細については、次を参照してください。 [変更パブリケーションとアーティクルのプロパティ](../../relational-databases/replication/publish/change-publication-and-article-properties.md)します。  
  
## すべてのパブリケーションのオプション  
  
### [作成と同期]  
 **[匿名サブスクリプションを許可]**  
 匿名プル サブスクリプションを許可するかどうかを決定します。 匿名サブスクリプションはサポートされて [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEWEd2005](../../includes/ssewed2005-md.md)], 、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssMobileEd2005](../../includes/ssmobileed2005-md.md)], 、および [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows CE 用です。 スナップショット レプリケーションおよびトランザクション パブリケーション、オプションは、このオプションを使用する **常に使用可能なスナップショット** に設定する必要があります **True**します。  
  
 **[アタッチ可能なサブスクリプション データベース]**  
 サブスクリプション データベースのコピーをアタッチすることでサブスクリプションを作成できるかどうかを判断 (する必要がありますオプション **常に使用可能なスナップショット** に設定されている **True** スナップショット レプリケーションおよびトランザクション パブリケーション)。  
  
> [!IMPORTANT]  
>  アタッチ可能なサブスクリプションは、将来のリリースでは使用できません。 この機能は推奨されません。  
  
 **[プル サブスクリプションを許可]**  
 サブスクライバーでこのパブリケーションのプル サブスクリプションを作成できるようにするかどうかを決定します。 詳細については、次を参照してください。 [パブリケーションをサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)します。  
  
### [スキーマ レプリケーション]  
 **[スキーマ変更のレプリケート]**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ。 パブリッシュされたオブジェクトに対して、テーブルへの列の追加や列のデータ型の変更などのスキーマ変更をレプリケートするかどうかを決定します。 詳細については、次を参照してください。 [パブリケーション データベースでスキーマ変更を行う](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)します。  
  
## スナップショット パブリケーションとトランザクション パブリケーションのオプション  
  
### [作成と同期]  
 **[独立したディストリビューション エージェント]**  
 このデータベースの他のパブリケーションから独立したエージェントを使用するかどうかを決定します。 このオプションは読み取り専用です。設定されている **True** 既定ではパブリケーションはパブリケーションの新規作成ウィザードで作成され、後は変更できませんパブリケーションを作成します。 詳細については、次を参照してください。 [レプリケーション エージェントの管理](../../relational-databases/replication/agents/replication-agent-administration.md)します。  
  
 **[スナップショットが常に利用可能]**  
 スナップショット エージェントが実行するたびに、スナップショット ファイルが作成されるかどうかを決定する (必要 **独立したディストリビューション エージェント**)。 このオプションは読み取り専用です。設定されている **True** を選択した場合 **スナップショットをすぐに作成し、サブスクリプションの初期化に使用可能なスナップショットを保持する** 上、 **スナップショット エージェント** 新規パブリケーション ウィザード (既定値) のページです。 詳細については、次を参照してください。 [を作成し、スナップショットの適用](../../relational-databases/replication/create-and-apply-the-snapshot.md)します。  
  
 **[バックアップ ファイルからの初期化を許可]**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ。 サブスクリプションの初期化でバックアップ ファイルを使用できるようにするかどうかを決定します。 詳細については、次を参照してください。 [、スナップショット トランザクション サブスクリプションなしの初期化](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)します。  
  
 **[SQL Server 以外のサブスクライバーを許可]**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ。 パブリケーションで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーをサポートするかどうかを決定します。 このオプションを設定 **True** をサポートするには、他のパブリケーション プロパティを設定するには非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーです。 このオプションは、サブスクリプションが存在する場合は読み取り専用設定できません **True** 場合 **即時更新サブスクリプションを許可する**, 、**キュー更新サブスクリプションを許可する**, 、または **ピア ツー ピア サブスクリプションを許可する** に設定されている **True**します。 詳細については、次を参照してください。 [非 SQL Server サブスクライバー](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)します。  
  
### [データの変換]  
 **[データ変換を許可]**  
 データをサブスクライバーに配布する前に、データ変換サービス (DTS) を使用してデータを変換するかどうかを決定します。 このオプションは読み取り専用であり、データの変換を有効にできるのは、ストアド プロシージャを使用してパブリケーションが作成された場合のみです。  
  
> [!IMPORTANT]  
>  変換可能なサブスクリプションは、将来のリリースでは使用できません。 この機能は推奨されません。  
  
### [ピア ツー ピア レプリケーション]  
 **[ピア ツー ピア サブスクリプションを許可]**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンにのみ適用されます。 パブリケーションでピア ツー ピア レプリケーションをサポートするかどうかを決定します。 このオプションを設定 **True** ピア ツー ピア レプリケーションをサポートするその他のパブリケーションのプロパティを設定します。 サブスクリプションが存在する場合、このオプションは読み取り専用です。 このオプションを設定できません **True** 場合 **即時更新サブスクリプションを許可する** または **キュー更新サブスクリプションを許可する**, 、または **SQL Server 以外のサブスクライバーを許可する** に設定されている **True**します。 詳細については、次を参照してください。 [ピア ツー ピア トランザクション レプリケーション](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)します。  
  
 **[ピア ツー ピア競合検出を許可]**  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンにのみ適用されます。 このパブリケーションで競合検出を有効にするかどうかを指定します。 競合検出を使用するには、すべてのノードが [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンを実行しており、すべてのノードで検出が有効になっている必要があります。 競合の検出を使用するのには、値も指定する必要があります **ピア実行者 id**します。 詳細については、次を参照してください。 [ピア ツー ピア レプリケーションで競合検出](../../relational-databases/replication/transactional/conflict-detection-in-peer-to-peer-replication.md)します。  
  
 **[ピア実行者 ID]**  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンにのみ適用されます。 ピア ツー ピア トポロジ内のノードの ID を指定します。 場合に、競合の検出にこの ID を使用 **ピア ツー ピア競合検出を使用する** に設定されている **True**します。 トポロジで使用されていないゼロ以外の正の ID を指定してください。 既に使用されている Id の一覧は、クエリ、 [Mspeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md) システム テーブルです。  
  
### [更新可能なサブスクリプション]  
 **[即時更新サブスクリプションを許可]**  
 サブスクライバーのデータ変更をパブリッシャーに即時にレプリケートできるかどうかを決定します。 このオプションは読み取り専用であり、更新サブスクリプションを有効にできるのは、パブリケーションが作成された場合のみです。 詳細については、次を参照してください。 [トランザクション レプリケーションの更新可能なサブスクリプション](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)します。  
  
 **[キュー更新サブスクリプションを許可]**  
 サブスクライバーのデータ変更をキューに登録しておき、後からパブリッシャーにレプリケートできるかどうかを決定します。 このオプションは読み取り専用であり、更新サブスクリプションを有効にできるのは、パブリケーションが作成された場合のみです。 詳細については、次を参照してください。 [トランザクション レプリケーションの更新可能なサブスクリプション](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)します。  
  
 **[競合を一元的にレポート]**  
 データ変更はパブリッシャーだけで、またはパブリッシャーとサブスクライバーの両方での競合を報告するかどうか (オプションを必要と **キュー更新サブスクリプションを許可する**)。 このオプションは読み取り専用です。設定されている **True** 既定ではパブリケーションはパブリケーションの新規作成ウィザードで作成され、後は変更できませんパブリケーションを作成します。 値 **True** はパブリッシャーだけで競合が報告されることを意味します。 競合は、レポートされた場所でのみ参照できます。  
  
 **[競合の解決方法]**  
 サブスクライバーの変更がパブリッシャーの変更と競合しているときに実行するアクションを指定します (オプションを必要と **キュー更新サブスクリプションを許可する**)。 詳細については、次を参照してください。 [の更新の競合検出のキューに登録および解決](../../relational-databases/replication/transactional/queued-updating-conflict-detection-and-resolution.md)します。  
  
 **[キューの種類]**  
 使用するかどうか、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] キューまたは [!INCLUDE[msCoName](../../includes/msconame-md.md)] メッセージ キュー (MSMQ) に変更をパブリッシャーに適用できるまで、サブスクライバーでキュー (、オプションが必要です **キュー更新サブスクリプションを許可する**)。 このオプションは [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] に対してのみ適用されます。それ以降のバージョンでは、キューイングに常に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルを使用します。  
  
## マージ パブリケーションのオプション  
  
### [競合に関するレポートの作成]  
 **[競合を一元的にレポート]**  
 パブリッシャーのみで、またはパブリッシャーとサブスクライバーの両方で、競合するデータ変更をレポートするかどうかを決定します このオプションは読み取り専用です。設定されている **True** 既定ではパブリケーションはパブリケーションの新規作成ウィザードで作成され、後は変更できませんパブリケーションを作成します。 値 **True** はパブリッシャーだけで競合が報告されることを意味します。 競合は、レポートされた場所でのみ参照できます。 詳細については、の [競合の表示] セクションを参照してください。 [マージ レプリケーション競合検出の詳細および解決](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)します。  
  
### フィルター  
 **[パラメーター化されたフィルターの許可]**  
 パラメーター化されたフィルターを、パブリケーションで使用するかどうかに基づいて設定します。 このオプションは常に読み取り専用です。 詳しくは、「 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-row-filters.md)」をご覧ください。  
  
 **[サブスクライバーの検証]**  
 サブスクライバーで、正しいデータのパーティションが保持されているかどうかを検証する場合に使用する関数を決定します。 複数の値がある場合はコンマで区切ります。 詳細については、次を参照してください。 [マージ サブスクライバーのパーティション情報の検証](../../relational-databases/replication/validate-partition-information-for-a-merge-subscriber.md)します。  
  
 **[パーティションの事前計算]**  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンのみ。 どのデータがどのパーティションに属しているかを事前に計算することによって、同期を最適化するかどうかを決定します。 この設定が既定で **True** パブリケーションが事前計算済みパーティションの条件を満たす場合。 詳細については、次を参照してください。 [事前計算済みパーティションを持つパラメーター化されたフィルター パフォーマンスの最適化](../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md)します。  
  
 **[同期の最適化]**  
 各サブスクライバーで追加メタデータを格納することによって、マージ プロセスを最適化するかどうかを決定します。 この最適化は事前計算済みパーティションによって置き換えられました **同期の最適化** オプションはのみ関連場合 **パーティションの事前計算** に設定されている **False**します。 詳しくは、「 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-row-filters.md)」をご覧ください。  
  
### [マージ プロセス]  
 **[同時実行プロセスの制限]**  
 同時に実行できるマージ エージェントの数を制限するかどうかを決定します。 通常は、パブリケーションが持つプッシュ サブスクリプションの中で、同時に同期する可能性のあるものが多い場合に使用されます。  
  
 **[最大同時プロセス数]**  
 同時に実行できるマージ エージェントの最大数 (必要 **同時実行プロセスの制限**)。 同期するエージェントの数が最大数を超えた場合は、数が最大数未満になるまでエージェントはキューに入れられます。  
  
## 参照  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  