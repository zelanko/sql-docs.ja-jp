---
title: マージ パブリケーションの競合情報の表示 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], viewing conflicts
- sp_helpmergeconflictrows
- viewing conflict information
- conflict resolution [SQL Server replication], merge replication
- sp_helpmergearticleconflicts
ms.assetid: 4907fe35-10ee-4f81-b924-fc419b1864d2
caps.latest.revision: 22
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 754a5c4bed2ba321987c4b0b820f4ad821369f42
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37351691"
---
# <a name="view-conflict-information-for-merge-publications"></a>マージ パブリケーションの競合情報の表示
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  マージ レプリケーションの競合を解決すると、優先されなかった行のデータが競合テーブルに書き込まれます。 この競合データは、レプリケーション ストアド プロシージャを使用してプログラムから表示できます。 詳細については、「 [マージ レプリケーションの競合検出および解決の詳細](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)」を参照してください。  
  
### <a name="to-view-conflict-information-and-losing-row-data-for-all-types-of-conflicts"></a>すべての種類の競合に関する競合情報と優先されなかった行のデータを表示するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して、 [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)を実行します。 結果セットで、次の列の値を確認します。  
  
    -   **centralized_conflicts** - 1 は競合する行がパブリッシャーに格納されていることを示し、0 は競合する行がパブリッシャーに格納されていないことを示します。  
  
    -   **decentralized_conflicts** - 1 は競合する行がサブスクライバーに格納されていることを示し、0 は競合する行がサブスクライバーに格納されていないことを示します。  
  
        > [!NOTE]  
        >  マージ パブリケーションの競合ログの動作は、 **@conflict_logging** の [@conflict_logging](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)」を参照してください。 Use of the **@centralized_conflicts** parameter has been deprecated.  
  
     次の表で、 **@conflict_logging**」を参照してください。  
  
    |@conflict_logging 値|centralized_conflicts|decentralized_conflicts|  
    |------------------------------|----------------------------|------------------------------|  
    |**パブリッシャー**|1|0|  
    |**サブスクライバー**|0|1|  
    |**両方**|1|1|  
  
2.  パブリッシャー側のパブリケーション データベースまたはサブスクライバー側のサブスクリプション データベースに対して、 [sp_helpmergearticleconflicts](../../relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql.md)を実行します。 特定のパブリケーションに属するアーティクルの競合情報のみが返されるようにするには、 **@publication** に値を指定します。 これにより、競合を持つアーティクルに対応する競合テーブル情報が返されます。 目的のアーティクルに対応する **conflict_table** の値を確認します。 アーティクルに対応する **conflict_table** の値が NULL の場合、そのアーティクル内では削除競合のみが発生しています。  
  
3.  (省略可) 目的のアーティクルで競合する行を確認します。 手順 1. の **centralized_conflicts** および **decentralized_conflicts** の値に応じて、次のいずれかの操作を実行します。  
  
    -   パブリッシャー側のパブリケーション データベースに対して、 [sp_helpmergeconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql.md)を実行します。 手順 1. で確認したアーティクルの競合テーブルを **@conflict_table**」を参照してください。 (省略可) 特定のパブリケーションの競合情報が返されるように制限するには、 **@publication** に値を指定します。 これにより、優先されなかった行の行データとその他の情報が返されます。  
  
    -   サブスクライバー側のサブスクリプション データベースに対して、 [sp_helpmergeconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergeconflictrows-transact-sql.md)を実行します。 手順 1. で確認したアーティクルの競合テーブルを **@conflict_table**」を参照してください。 これにより、優先されなかった行の行データとその他の情報が返されます。  
  
### <a name="to-view-information-only-on-conflicts-where-the-delete-failed"></a>削除の失敗による競合に関する情報のみを表示するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して、 [sp_helpmergepublication](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)を実行します。 結果セットで、次の列の値を確認します。  
  
    -   **centralized_conflicts** - 1 は競合する行がパブリッシャーに格納されていることを示し、0 は競合する行がパブリッシャーに格納されていないことを示します。  
  
    -   **decentralized_conflicts** - 1 は競合する行がサブスクライバーに格納されていることを示し、0 は競合する行がサブスクライバーに格納されていないことを示します。  
  
        > [!NOTE]  
        >  マージ パブリケーションの競合ログの動作は、 **@conflict_logging** の [@conflict_logging](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)」を参照してください。 Use of the **@centralized_conflicts** parameter has been deprecated.  
  
2.  パブリッシャー側のパブリケーション データベースまたはサブスクライバー側のサブスクリプション データベースに対して、 [sp_helpmergearticleconflicts](../../relational-databases/system-stored-procedures/sp-helpmergearticleconflicts-transact-sql.md)を実行します。 特定のパブリケーションに属するアーティクルの競合情報のみが返されるようにするには、 **@publication** に値を指定します。 これにより、競合を持つアーティクルに対応する競合テーブル情報が返されます。 目的のアーティクルに対応する **source_object** の値を確認します。 アーティクルに対応する **conflict_table** の値が NULL の場合、そのアーティクル内では削除競合のみが発生しています。  
  
3.  (省略可) 削除競合の競合情報を確認します。 手順 1. の **centralized_conflicts** および **decentralized_conflicts** の値に応じて、次のいずれかの操作を実行します。  
  
    -   パブリッシャー側のパブリケーション データベースに対して、 [sp_helpmergedeleteconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql.md)を実行します。 手順 1. で確認した、競合が発生しているソース テーブルの名前を **@source_object**」を参照してください。 (省略可) 特定のパブリケーションの競合情報が返されるように制限するには、 **@publication** に値を指定します。 これにより、パブリッシャーに格納されている削除競合の情報が返されます。  
  
    -   サブスクライバー側のサブスクリプション データベースに対して、 [sp_helpmergedeleteconflictrows](../../relational-databases/system-stored-procedures/sp-helpmergedeleteconflictrows-transact-sql.md)を実行します。 手順 1. で確認した、競合が発生しているソース テーブルの名前を **@source_object**」を参照してください。 (省略可) 特定のパブリケーションの競合情報が返されるように制限するには、 **@publication** に値を指定します。 これにより、サブスクライバーに格納されている削除競合の情報が返されます。  
  
## <a name="see-also"></a>参照  
 [マージ レプリケーションの競合検出および解決の詳細](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
