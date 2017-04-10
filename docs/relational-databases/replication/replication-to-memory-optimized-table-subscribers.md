---
title: "メモリ最適化テーブル サブスクライバーへのレプリケーション | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "11/21/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1a8e6bc7-433e-471d-b646-092dc80a2d1a
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# メモリ最適化テーブル サブスクライバーへのレプリケーション
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  スナップショットとトランザクション レプリケーション サブスクライバーとして機能するテーブルは、ピア ツー ピア トランザクション レプリケーションを除き、メモリ最適化テーブルとして構成できます。 その他のレプリケーション構成はメモリ最適化テーブルとは互換性がありません。 この機能は [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]以降のバージョンで使用できます。  
  
## <a name="two-configurations-are-required"></a>必要な 2 つの構成  
  
-   **メモリ最適化テーブルへのレプリケーションをサポートするためにサブスクライバー データベースを構成します。**  
  
     設定、 **@memory_optimized** プロパティを **true**, を使用して [sp_addsubscription & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) または [sp_changesubscription & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-changesubscription-transact-sql.md)します。  
  
-   **メモリ最適化テーブルへのレプリケーションをサポートするアーティクルを構成します。**  
  
     設定、 `@schema_option = 0x40000000000` オプションを使用してアーティクルの [sp_addarticle & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md) または [sp_changearticle & #40 です。Transact SQL と #41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)します。  
  
#### <a name="to-configure-a-memory-optimized-table-as-a-subscriber"></a>メモリ最適化テーブルをサブスクライバーとして構成するには  
  
1.  トランザクション パブリケーションを作成します。 詳細については、「 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)」を参照してください。  
  
2.  パブリケーションにアーティクルを追加します。 詳しくは、「 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
     使用して構成する場合は、 [!INCLUDE[tsql](../../includes/tsql-md.md)] 設定、 **@schema_option** のパラメーター、 **sp_addarticle** ストアド プロシージャを   
    **0x40000000000**以降のバージョンで使用できます。  
  
3.  [アーティクルのプロパティ] ウィンドウで **[Enable Memory optimization]** (メモリ最適化を有効にする) を **true**に設定します。  
  
4.  スナップショット エージェント ジョブを起動して、このパブリケーションの初期スナップショットを生成します。 詳細については、「 [Create and Apply the Initial Snapshot](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)」を参照してください。  
  
5.  ここで、新しいサブスクリプションを作成します。 **サブスクリプションの新規作成ウィザード** で **[Memory Optimized Subscription]** (メモリ最適化サブスクリプション) を **true**に設定します。  
  
 これでメモリ最適化テーブルはパブリッシャーから更新を受け取り始めます。  
  
#### <a name="reconfigure-an-existing-transaction-replication"></a>既存のトランザクション レプリケーションを再構成する  
  
1.  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] のサブスクリプションのプロパティに移動して、 **[Memory Optimized Subscription]** (メモリ最適化サブスクリプション) を **true**に設定します。 サブスクリプションを再初期化するまで変更は適用されません。  
  
     使用して構成する場合は、 [!INCLUDE[tsql](../../includes/tsql-md.md)] 設定、新しい **@memory_optimized** のパラメーター、 **sp_addsubscription** ストアド プロシージャを true にします。  
  
2.  	[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] でパブリケーションのアーティクルのプロパティに移動して、 **[Enable Memory optimization]** (メモリ最適化を有効にする) を true に設定します。  
  
     使用して構成する場合は、 [!INCLUDE[tsql](../../includes/tsql-md.md)] 設定、 **@schema_option** のパラメーター、 **sp_addarticle** ストアド プロシージャを   
    **0x40000000000**以降のバージョンで使用できます。  
  
3.  クラスター化インデックスは、メモリ最適化テーブルでサポートされていません。 レプリケーションにこれを処理させるには、変換先で非クラスター化インデックスに変換します。そのためには、 **[Convert clustered index to nonclustered for memory optimized article]** (クラスター化インデックスをメモリ最適化アーティクル向けに非クラスター化インデックスに変換する) を true に設定します。  
  
     使用して構成する場合は、 [!INCLUDE[tsql](../../includes/tsql-md.md)] 設定、 **@schema_option** のパラメーター、 **sp_addarticle** ストアド プロシージャを  **0x0000080000000000**します。  
  
4.  スナップショットを再生成します。  
  
5.  サブスクリプションを再初期化します。  
  
## <a name="remarks-and-restrictions"></a>解説と制限事項  
 一方向トランザクション レプリケーションのみがサポートされています。 ピア ツー ピア トランザクション レプリケーションはサポートされていません。  
  
 メモリ最適化テーブルをパブリッシュすることはできません。  
  
 ディストリビューターのレプリケーション テーブルをメモリ最適化テーブルとして構成することはできません。  
  
 マージ レプリケーションにメモリ最適化テーブルを含めることはできません。  
  
 サブスクライバーで、トランザクション レプリケーションにかかわるテーブルをメモリ最適化テーブルとして構成できますが、サブスクライバーのテーブルはメモリ最適化テーブルの要件を満たす必要があります。 この場合の制限事項は次のとおりです。  
 
-   サブスクライバーのメモリ最適化テーブルにレプリケートされるテーブルは、メモリ最適化テーブルに使用できるデータ型に制限されます。 詳細については、「 [サポートされるデータ型](../../relational-databases/in-memory-oltp/supported-data-types-for-in-memory-oltp.md)」を参照してください。  
  
-   メモリ最適化テーブルでは、すべての TRANSACT-SQL 機能がサポートされています。 参照してください [Transact SQL を構築、インメモリ OLTP でサポートされていない](../../relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md) 詳細です。  
  
##  <a name="a-nameschemaa-modifying-a-schema-file"></a><a name="Schema"></a> スキーマ ファイルの変更  
  
-   メモリ最適化テーブルのオプション `DURABILITY = SCHEMA_AND_DATA` を使用する場合、テーブルには非クラスター化主キー インデックスが必要です。  
  
-   ANSI_PADDING は ON にする必要があります。  
  
## <a name="see-also"></a>参照  
 [レプリケーション機能とタスク](../../relational-databases/replication/replication-features-and-tasks.md)  
  
  