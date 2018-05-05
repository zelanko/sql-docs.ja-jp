---
title: sp_mergecleanupmetadata (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_mergecleanupmetadata_TSQL
- sp_mergecleanupmetadata
helpviewer_keywords:
- sp_mergecleanupmetadata
ms.assetid: 892f8628-4cbe-4cc3-b959-ed45ffc24064
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 026675528003028ffd3fd73301f47f75bcab0575
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spmergecleanupmetadata-transact-sql"></a>sp_mergecleanupmetadata (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  バージョンを実行するサーバーを含むレプリケーション トポロジでのみ使用する必要があります[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]より前のバージョン[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]Service Pack 1 **。sp_mergecleanupmetadata**でメタデータをクリーンアップすることができます、 **MSmerge_genhistory**、 **MSmerge_contents**と**MSmerge_tombstone**システム テーブル。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_mergecleanupmetadata [ [ @publication = ] 'publication' ]  
    [ , [ @reinitialize_subscriber = ] 'reinitialize_subscriber' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication =** ] **'***publication***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値は**%**、すべてのパブリケーションのメタデータをクリーンアップします。 パブリケーションを明示的に指定する場合は、これが既に存在している必要があります。  
  
 [  **@reinitialize_subscriber =** ] **'***サブスクライバー***'**  
 サブスクライバーを再初期化するかどうかを指定します。 *サブスクライバー*は**nvarchar (5)** を指定できます**TRUE**または**FALSE**、既定値は**TRUE**です。 場合**TRUE**サブスクリプションが再初期化のマークが付けします。 場合**FALSE**サブスクリプションが再初期化のマークされていません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_mergecleanupmetadata**のバージョンを実行するサーバーを含むレプリケーション トポロジでのみ使用する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]より前のバージョン[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]Service Pack 1。 のみが含まれるトポロジ[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]Service Pack 1 またはそれ以降は、自動保有期間に基づくメタデータのクリーンアップを使用する必要があります。 このストアド プロシージャを実行する場合は、実行するコンピューター上で、きわめて大きいログファイルが必要であり、作成される可能性があることに注意してください。  
  
> [!CAUTION]  
>  後に**sp_mergecleanupmetadata**が実行される、既定に格納されるメタデータを持つパブリケーションのサブスクライバーのすべてのサブスクリプション**MSmerge_genhistory**、 **MSmerge_contents**と**MSmerge_tombstone**とマークされて、再初期化のサブスクライバーの保留中の変更は失われ、現在のスナップショットが obsolete としてマークします。  
  
> [!NOTE]  
>  かどうか、データベースで複数のパブリケーションが存在し、それらのパブリケーションのいずれかが無期限のパブリケーション保有期間を使用して (**@retention**=**0**) 実行中、 **sp_mergecleanupmetadata**クリーンアップ、マージ レプリケーション変更の追跡データベースのメタデータがありません。 このため、無期限のパブリケーション保有期間は注意して使用してください。  
  
 これを実行すると、プロシージャが格納されている、ときに、サブスクライバーを再初期化を設定するかどうかを選択できます、 **@reinitialize_subscriber**パラメーターを**TRUE** (既定) または**FALSE**. 場合**sp_mergecleanupmetadata**を実行すると、 **@reinitialize_subscriber**パラメーターに設定**TRUE**サブスクリプションがいた場合でも、サブスクライバーでスナップショットが再適用されます初期スナップショット (たとえば場合、スナップショットやデータとスキーマが手動で適用される、サブスクライバーに既に存在していた) なしで作成します。 パラメータを設定する**FALSE**パブリケーションが再初期化されていない場合、パブリッシャーとサブスクライバーでデータが同期されていることを確認する必要がありますので、注意、して使用する必要があります。  
  
 値に関係なく**@reinitialize_subscriber**、 **sp_mergecleanupmetadata**が継続的なエラーが発生、パブリッシャーまたは再パブリッシュ サブスクライバーに変更をアップロードしようとしているプロセスのマージストアド プロシージャが呼び出された時刻。  
  
 **Sp_mergecleanupmetadata の実行@reinitialize_subscriber= TRUE:**  
  
1.  パブリケーション データベースとサブスクリプション データベースに対するすべての更新を中止することをお勧めしますが必須ではありません。 更新を続行すると、パブリケーションが再初期化される際に、前回のマージ以降にサブスクライバー側で行われたすべての更新が失われますが、データの収束は保持されます。  
  
2.  マージ エージェントを実行してマージを実行します。 使用することをお勧め、 **– Validate**マージ エージェントを実行すると、各サブスクライバーでエージェントのコマンド ライン オプションです。 連続モードのマージを実行している場合は、次を参照してください。*連続モードのマージに関する注意事項*このセクションで後述します。  
  
3.  すべてのマージが完了したら、実行**sp_mergecleanupmetadata**です。  
  
4.  実行**sp_reinitmergepullsubscription**名前付きまたは匿名のプル サブスクリプションを使用してデータを収束させることを確認するすべてのサブスクライバーにします。  
  
5.  連続モードのマージを実行している場合は、次を参照してください。*連続モードのマージに関する注意事項*このセクションで後述します。  
  
6.  すべてのレベルで関係するすべてのマージ パブリケーションに対して、スナップショット ファイルを再生成します。 最初にスナップショットを再生成せずにマージしようとすると、スナップショットを再生成するように要求されます。  
  
7.  パブリケーション データベースをバックアップします。 先にバックアップを実行すると、パブリケーション データベースの復元後にマージが失敗する可能性があります。  
  
 **Sp_mergecleanupmetadata の実行@reinitialize_subscriber= FALSE。**  
  
1.  停止**すべて**パブリケーションおよびサブスクリプション データベースを更新します。  
  
2.  マージ エージェントを実行してマージを実行します。 使用することをお勧め、 **– Validate**マージ エージェントを実行すると、各サブスクライバーでエージェントのコマンド ライン オプションです。 連続モードのマージを実行している場合は、次を参照してください。*連続モードのマージに関する注意事項*このセクションで後述します。  
  
3.  すべてのマージが完了したら、実行**sp_mergecleanupmetadata**です。  
  
4.  連続モードのマージを実行している場合は、次を参照してください。*連続モードのマージに関する注意事項*このセクションで後述します。  
  
5.  すべてのレベルで関係するすべてのマージ パブリケーションに対して、スナップショット ファイルを再生成します。 最初にスナップショットを再生成せずにマージしようとすると、スナップショットを再生成するように要求されます。  
  
6.  パブリケーション データベースをバックアップします。 先にバックアップを実行すると、パブリケーション データベースの復元後にマージが失敗する可能性があります。  
  
 **連続モードのマージに関する注意事項**  
  
 連続モードのマージを実行する場合は、次のいずれかの操作を行う必要があります。  
  
-   マージ エージェントを停止してせずに別のマージを実行して、 **-連続**パラメーターが指定されています。  
  
-   パブリケーションを非アクティブ化**sp_changemergepublication**をパブリケーションの状態をポーリングしている連続モードのマージが失敗することを確認します。  
  
    ```  
    EXEC central..sp_changemergepublication @publication = 'dynpart_pubn', @property = 'status', @value = 'inactive'  
    ```  
  
 完了したときの実行手順 3. **sp_mergecleanupmetadata**、停止した方法に基づいて連続モードのマージを再開します。 次のいずれかの操作を行います。  
  
-   追加、 **– Continuous**マージ エージェントのパラメーターです。  
  
-   パブリケーションを再アクティブ化**sp_changemergepublication です。**  
  
    ```  
    EXEC central..sp_changemergepublication @publication = 'dynpart_pubn', @property = 'status', @value = 'active'  
    ```  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_mergecleanupmetadata**です。  
  
 このストアド プロシージャを使用するには、パブリッシャーが [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] を実行していることが必要です。 いずれかのサブスクライバーを実行する必要があります[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]または[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 では、Service Pack 2 です。  
  
## <a name="see-also"></a>参照  
 [MSmerge_genhistory &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/msmerge-genhistory-transact-sql.md)   
 [MSmerge_contents &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/msmerge-contents-transact-sql.md)   
 [MSmerge_tombstone &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/msmerge-tombstone-transact-sql.md)  
  
  
