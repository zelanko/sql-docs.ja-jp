---
title: "sp_reinitsubscription (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_reinitsubscription
- sp_reinitsubscription_TSQL
helpviewer_keywords: sp_reinitsubscription
ms.assetid: d56ae218-6128-4ff9-b06c-749914505c7b
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 28ed672409e115b5b7980766ee7bf078d52b3bf1
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spreinitsubscription-transact-sql"></a>sp_reinitsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サブスクリプションに再初期化のマークを付けます。 このストアド プロシージャは、プッシュ サブスクリプションのパブリッシャー側で実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_reinitsubscription [ [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
        , [ @subscriber = ] 'subscriber'  
    [ , [ @destination_db = ] 'destination_db']  
    [ , [ @for_schema_change = ] 'for_schema_change']  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @ignore_distributor_failure = ] ignore_distributor_failure ]   
    [ , [ @invalidate_snapshot = ] invalidate_snapshot ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication=**] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値は all です。  
  
 [  **@article=**] **'***記事***'**  
 アーティクルの名前を指定します。 *記事*は**sysname**、既定値は all です。 即時更新パブリケーションの場合*記事*する必要があります**すべて**以外の場合、ストアド プロシージャは、パブリケーションをスキップし、エラーを報告します。  
  
 [  **@subscriber=**] **'***サブスクライバー***'**  
 サブスクライバーの名前です。 *サブスクライバー*は**sysname**、既定値はありません。  
  
 [  **@destination_db=**] **'***destination_db***'**  
 対象データベース名を指定します。 *destination_db*は**sysname**、既定値は all です。  
  
 [  **@for_schema_change=**] **'***for_schema_change***'**  
 パブリケーション データベースでスキーマを変更した結果として、再初期化が行われるかどうかを指定します。 *for_schema_change*は**ビット**、既定値は 0 です。 場合**0**、即時更新を許可するパブリケーションにアクティブなサブスクリプションがパブリケーション全体と、アーティクルの一部だけでなくが再初期化される限り、再アクティブ化します。 これは、スキーマ変更の結果、再初期化が行われることを表します。 場合**1**、スナップショット エージェントが実行されるまでにないアクティブなサブスクリプションが再アクティブ化します。  
  
 [  **@publisher=** ] **'***パブリッシャー***'**  
 指定以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*を使用しないで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
 [  **@ignore_distributor_failure=** ] *ignore_distributor_failure*  
 ディストリビューターが存在しないかオフラインの場合でも、再初期化を許可します。 *ignore_distributor_failure*は**ビット**、既定値は 0 です。 場合**0**ディストリビューターが存在しないかオフラインになっている場合に再初期化が失敗します。  
  
 [  **@invalidate_snapshot=** ] *invalidate_snapshot*  
 既存のパブリケーション スナップショットを無効にします。 *invalidate_snapshot*は**ビット**、既定値は 0 です。 場合**1**パブリケーションの新しいスナップショットを生成します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_reinitsubscription**トランザクション レプリケーションで使用します。  
  
 **sp_reinitsubscription**ピア ツー ピア トランザクション レプリケーションはサポートされていません。  
  
 初期スナップショットが自動的に適用され、パブリケーションで更新可能なサブスクリプションが許可されない場合のサブスクリプションについては、このストアド プロシージャを実行してからスナップショット エージェントを実行する必要があります。こうすると、スキーマおよび一括コピー プログラム ファイルの準備ができてから、ディストリビューション エージェントでサブスクリプションを再同期化できます。  
  
 初期スナップショットが自動的に適用され、パブリケーションで更新可能なサブスクリプションが許可される場合のサブスクリプションについては、ディストリビューション エージェントでサブスクリプションを再同期化するときに、スナップショット エージェントによって以前に作成された最新のスキーマおよび一括コピー プログラム ファイルが使用されます。 ユーザーを実行した直後に、ディストリビューション エージェントがサブスクリプションを再同期化**sp_reinitsubscription**ディストリビューション エージェントがビジーでない、それ以外の場合、メッセージの間隔 (後の同期が発生する場合は、ディストリビューション エージェント コマンド プロンプト パラメーターで指定された: **MessageInterval**)。  
  
 **sp_reinitsubscription**も何も起こりませんのサブスクリプションの初期スナップショットが手動で適用される場所です。  
  
 パブリケーションへの匿名サブスクリプションを再同期を渡します**すべて**またはとして NULL*サブスクライバー*です。  
  
 トランザクション レプリケーションでは、アーティクル レベルでのサブスクリプションの再初期化がサポートされます。 アーティクルに再初期化のマークが付けられると、次の同期化の際に、アーティクルのスナップショットがサブスクライバーで再適用されます。 ただし、同じサブスクライバーにサブスクライブされる従属アーティクルがある場合は、特定の状況でパブリケーション内の従属アーティクルも自動的に再初期化されない限り、アーティクルへのスナップショットの再適用は失敗する可能性があります。  
  
-   アーティクルの事前作成コマンドが "drop" の場合、そのアーティクルのベース オブジェクトのスキーマ バインド ビューとスキーマ バインド ストアド プロシージャに対応するアーティクルにも、再初期化のマークが付けられます。  
  
-   アーティクルのスキーマ オプションに、主キーに関する宣言済みの参照整合性のスクリプト作成が含まれている場合は、再初期化されるアーティクルのベース テーブルに対して、外部キー リレーションシップが設定されているベース テーブルを持つアーティクルにも、再初期化のマークが付けられます。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_reinittranpushsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitsubscription-tr_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**のメンバー、固定サーバー ロール、 **db_owner**固定データベース ロール、またはサブスクリプションの作成者が実行できる**sp_reinitsubscription**.  
  
## <a name="see-also"></a>参照  
 [サブスクリプションの再初期化](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [サブスクリプションの再初期化](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
