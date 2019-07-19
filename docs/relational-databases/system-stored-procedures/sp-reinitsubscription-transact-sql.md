---
title: sp_reinitsubscription (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_reinitsubscription
- sp_reinitsubscription_TSQL
helpviewer_keywords:
- sp_reinitsubscription
ms.assetid: d56ae218-6128-4ff9-b06c-749914505c7b
author: stevestein
ms.author: sstein
ms.openlocfilehash: 85911e4ce5652d15b99be4d87f75a04214a7f854
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68075641"
---
# <a name="spreinitsubscription-transact-sql"></a>sp_reinitsubscription (TRANSACT-SQL)
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
`[ @publication = ] 'publication'` パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値は all です。  
  
`[ @article = ] 'article'` アーティクルの名前です。 *記事*は**sysname**、既定値は all です。 即時更新パブリケーションの場合*記事*必要があります**すべて**。 そうしないと、ストアド プロシージャは、パブリケーションをスキップし、エラーを報告します。  
  
`[ @subscriber = ] 'subscriber'` サブスクライバーの名前です。 *サブスクライバー*は**sysname**、既定値はありません。  
  
`[ @destination_db = ] 'destination_db'` 転送先データベースの名前です。 *destination_db*は**sysname**、既定値は all です。  
  
`[ @for_schema_change = ] 'for_schema_change'` 再初期化がパブリケーション データベースでスキーマ変更の結果として発生するかどうかを示します。 *for_schema_change*は**ビット**、既定値は 0。 場合**0**、パブリケーション全体とその記事では、一部だけでなくが再初期化される限り、即時更新を許可するパブリケーションにアクティブなサブスクリプションが再アクティブ化されます。 これは、スキーマ変更の結果、再初期化が開始されることを意味します。 場合**1**、スナップショット エージェントが実行されるまでにないアクティブなサブスクリプションが再アクティブ化します。  
  
`[ @publisher = ] 'publisher'` 以外を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*の使わないで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
`[ @ignore_distributor_failure = ] ignore_distributor_failure` ディストリビューターが存在しないかオフラインになっていて、再初期化を許可します。 *ignore_distributor_failure*は**ビット**、既定値は 0。 場合**0**ディストリビューターが存在しないかオフラインになっている場合に再初期化が失敗します。  
  
`[ @invalidate_snapshot = ] invalidate_snapshot` 既存のパブリケーションのスナップショットを無効にします。 *invalidate_snapshot*は**ビット**、既定値は 0。 場合**1**パブリケーションの新しいスナップショットを生成します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_reinitsubscription**はトランザクション レプリケーションで使用します。  
  
 **sp_reinitsubscription**ピア ツー ピア トランザクション レプリケーションはサポートされていません。  
  
 スキーマおよび一括コピー プログラム ファイルを準備するため、このストアド プロシージャが実行された後にサブスクリプションの場合、初期スナップショットがパブリケーションが更新可能なサブスクリプションを許可しないと自動的に適用される場合、スナップショット エージェントを実行する必要があります。され、ディストリビューション エージェントは、サブスクリプションを再同期できません。  
  
 初期スナップショットが自動的に適用され、パブリケーションで更新可能なサブスクリプションが許可される場合のサブスクリプションについては、ディストリビューション エージェントでサブスクリプションを再同期化するときに、スナップショット エージェントによって以前に作成された最新のスキーマおよび一括コピー プログラム ファイルが使用されます。 ユーザーが実行した直後に、ディストリビューション エージェントがサブスクリプションを再同期化**sp_reinitsubscription**ディストリビューション エージェントがビジー状態ですそれ以外の同期が、メッセージの間隔 (後に発生する可能性がある場合は、。ディストリビューション エージェント コマンド プロンプト パラメーターで指定します。**MessageInterval**)。  
  
 **sp_reinitsubscription**何も起こりませんサブスクリプション、初期スナップショットが手動で適用される場所。  
  
 パブリケーションへの匿名サブスクリプションを再同期に渡す**すべて**として NULL または*サブスクライバー*します。  
  
 トランザクション レプリケーションでは、アーティクル レベルでのサブスクリプションの再初期化がサポートされます。 アーティクルに再初期化のマークが付けられると、次の同期化の際に、アーティクルのスナップショットがサブスクライバーで再適用されます。 ただし、同じサブスクライバーにサブスクライブされる従属アーティクルがある場合は、特定の状況でパブリケーション内の従属アーティクルも自動的に再初期化されない限り、アーティクルへのスナップショットの再適用は失敗する可能性があります。  
  
-   アーティクルの事前作成コマンドがある場合は、'drop'、スキーマ バインド ビューの記事とも、再初期化はスキーマ バインド ストアド プロシージャ アーティクルのベース オブジェクトに設定されています。  
  
-   アーティクルのスキーマ オプションに、主キーに関する宣言済みの参照整合性のスクリプト作成が含まれている場合は、再初期化されるアーティクルのベース テーブルに対して、外部キー リレーションシップが設定されているベース テーブルを持つアーティクルにも、再初期化のマークが付けられます。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_reinittranpushsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitsubscription-tr_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**のメンバー、固定サーバー ロール、 **db_owner**固定データベース ロール、またはサブスクリプションの作成者が実行できる**sp_reinitsubscription**.  
  
## <a name="see-also"></a>関連項目  
 [サブスクリプションの再初期化](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [サブスクリプションの再初期化](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
