---
title: "マージ パブリケーションの競合情報の表示 (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
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
  - "マージ レプリケーションの競合回避 [SQL Server レプリケーション], 競合の表示"
  - "sp_helpmergeconflictrows"
  - "競合情報の表示"
  - "競合回避 [SQL Server レプリケーション]、マージ レプリケーション"
  - "sp_helpmergearticleconflicts"
ms.assetid: 4907fe35-10ee-4f81-b924-fc419b1864d2
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# マージ パブリケーションの競合情報の表示 (レプリケーション Transact-SQL プログラミング)
  マージ レプリケーションの競合を解決すると、優先されなかった行のデータが競合テーブルに書き込まれます。 この競合データは、レプリケーション ストアド プロシージャを使用してプログラムから表示できます。 詳細については、「 [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)」を参照してください。  
  
### すべての種類の競合に関する競合情報と優先されなかった行のデータを表示するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)します。 結果セットで、次の列の値を確認します。  
  
    -   **centralized_conflicts** -1 ことを示し、パブリッシャーに競合する行が格納されている 0 は競合する行がパブリッシャーに格納されないことを示します。  
  
    -   **decentralized_conflicts** -1 ことを示し、サブスクライバーで競合する行が格納されている 0 は競合する行がサブスクライバーで格納されないことを示します。  
  
        > [!NOTE]  
        >  使用してマージ パブリケーションの競合のログ記録の動作を設定、 **@conflict_logging** のパラメーター [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)します。 使用、 **@centralized_conflicts** パラメーターは廃止されました。  
  
     次の表に、指定された値に基づいてこれらの列の値 **@conflict_logging**します。  
  
    |@conflict_logging の値|centralized_conflicts|decentralized_conflicts|  
    |------------------------------|----------------------------|------------------------------|  
    |**publisher **|1|0|  
    |**サブスクライバー (subscriber)**|0|1|  
    |**both**|1|1|  
  
2.  パブリケーション データベースのパブリッシャー側で、またはサブスクライバー側でサブスクリプション データベースが実行される [sp_helpmergearticleconflicts](../../relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql.md)します。 値を指定 **@publication** 単に特定のパブリケーションに属するアーティクルの競合情報を返すようにします。 これにより、競合を持つアーティクルに対応する競合テーブル情報が返されます。 値に注意してください **conflict_table** 目的のアーティクルにします。 場合の値 **conflict_table** 削除競合のみがこの記事で発生したアーティクルが NULL にします。  
  
3.  (省略可) 目的のアーティクルで競合する行を確認します。 値に応じて **centralized_conflicts** と **decentralized_conflicts** 手順 1 から、次のいずれかの操作を行います。  
  
    -   パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helpmergeconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql.md)します。 (ステップ 1) からのアーティクルの競合テーブルを指定して **@conflict_table**します。 (省略可能)値を指定して **@publication** 特定のパブリケーションに返される競合情報を制限します。 これにより、優先されなかった行の行データとその他の情報が返されます。  
  
    -   サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_helpmergeconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql.md)します。 (ステップ 1) からのアーティクルの競合テーブルを指定して **@conflict_table**します。 これにより、優先されなかった行の行データとその他の情報が返されます。  
  
### 削除の失敗による競合に関する情報のみを表示するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)します。 結果セットで、次の列の値を確認します。  
  
    -   **centralized_conflicts** -1 ことを示し、パブリッシャーに競合する行が格納されている 0 は競合する行がパブリッシャーに格納されないことを示します。  
  
    -   **decentralized_conflicts** -1 ことを示し、サブスクライバーで競合する行が格納されている 0 は競合する行がサブスクライバーで格納されないことを示します。  
  
        > [!NOTE]  
        >  使用してマージ パブリケーションの競合のログ記録の動作を設定、 **@conflict_logging** のパラメーター [sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)します。 使用、 **@centralized_conflicts** パラメーターは廃止されました。  
  
2.  パブリケーション データベースのパブリッシャー側で、またはサブスクライバー側でサブスクリプション データベースが実行される [sp_helpmergearticleconflicts](../../relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql.md)します。 値を指定 **@publication** 単に特定のパブリケーションに属するアーティクルの競合テーブル情報を返すようにします。 これにより、競合を持つアーティクルに対応する競合テーブル情報が返されます。 値に注意してください **source_object** 目的のアーティクルにします。 場合の値 **conflict_table** 削除競合のみがこの記事で発生したアーティクルが NULL にします。  
  
3.  (省略可) 削除競合の競合情報を確認します。 値に応じて **centralized_conflicts** と **decentralized_conflicts** 手順 1 から、次のいずれかの操作を行います。  
  
    -   パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_helpmergedeleteconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql.md)します。 競合の発生する (ステップ 1) からソース テーブルの名前を指定 **@source_object**します。 (省略可能)値を指定して **@publication** 特定のパブリケーションに返される競合情報を制限します。 これにより、パブリッシャーに格納されている削除競合の情報が返されます。  
  
    -   サブスクライバー サブスクリプション データベースで、次のように実行します。 [sp_helpmergedeleteconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql.md)します。 競合の発生する (ステップ 1) からソース テーブルの名前を指定 **@source_object**します。 (省略可能)値を指定して **@publication** 特定のパブリケーションに返される競合情報を制限します。 これにより、サブスクライバーに格納されている削除競合の情報が返されます。  
  
## 参照  
 [マージ レプリケーションの競合検出および解決の詳細](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  