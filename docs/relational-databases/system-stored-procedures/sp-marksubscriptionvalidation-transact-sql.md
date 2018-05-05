---
title: sp_marksubscriptionvalidation (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
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
- sp_marksubscriptionvalidation
- sp_marksubscriptionvalidation_TSQL
helpviewer_keywords:
- sp_marksubscriptionvalidation
ms.assetid: e68fe0b9-5993-4880-917a-b0f661f8459b
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 1b088b43cfc625591d5160b6818949b0c933a696
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spmarksubscriptionvalidation-transact-sql"></a>sp_marksubscriptionvalidation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在開いているトランザクションに、指定のサブスクライバーのサブスクリプションレベル検証トランザクションであることを示すマークを付けます。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_marksubscriptionvalidation [ @publication = ] 'publication'  
        , [ @subscriber = ] 'subscriber'  
        , [ @destination_db = ] 'destination_db'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication**=] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [ **@subscriber**=] **'***サブスクライバー***'**  
 サブスクライバーの名前です。 *サブスクライバー*は sysname で、既定値はありません。  
  
 [  **@destination_db=**] **'***destination_db***'**  
 対象データベース名を指定します。 *destination_db*は**sysname**、既定値はありません。  
  
 [  **@publisher=** ] **'***パブリッシャー***'**  
 指定以外[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*に属しているパブリケーションに対しては使用できません、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_marksubscriptionvalidation**トランザクション レプリケーションで使用します。  
  
 **sp_marksubscriptionvalidation**はサポートされません以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーです。  
  
 非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]実行することはできません、発行元**sp_marksubscriptionvalidation**から明示的なトランザクションです。 これは、パブリッシャーへのアクセスに使用されるリンク サーバー接続で、明示的なトランザクションがサポートされないためです。  
  
 **sp_marksubscriptionvalidation**と組み合わせて使用する必要があります[sp_article_validation &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md)の値を指定する**1**の*subscription_level*とには、その他の呼び出しで使用できます**sp_marksubscriptionvalidation**を他のサブスクライバーの現在開いているトランザクションをマークします。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_marksubscriptionvalidation**です。  
  
## <a name="example"></a>例  
 次のクエリは、サブスクリプションレベルの検証コマンドを通知するために、パブリッシング データベースに適用できます。 これらのコマンドは、指定されたサブスクライバーのディストリビューション エージェントによって処理されます。 最初のトランザクションがアーティクルを検証することに注意してください '**art1**'、トランザクションの検証中、2 番目に'**art2**' です。 なおへの呼び出し**sp_marksubscriptionvalidation**と[sp_article_validation &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md)トランザクションにカプセル化されました。 1 つだけの呼び出しをお勧め[sp_article_validation &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md) (トランザクションあたり)。 これは、ため[sp_article_validation &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md)トランザクションの実行中、ソース テーブルで、共有テーブル ロックを保持します。 同時実行性を最大限に高めるために、トランザクションは短くしてください。  
  
```  
begin tran  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub', @destination_db = 'SubDB'  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub2', @destination_db = 'SubDB'  
  
exec sp_article_validation @publication = 'pub1', @article = 'art1',  
 @rowcount_only = 0, @full_or_fast = 0, @shutdown_agent = 0,  
 @subscription_level = 1  
  
commit tran  
  
begin tran  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub', @destination_db = 'SubDB'  
  
exec sp_marksubscriptionvalidation @publication = 'pub1',  
 @subscriber = 'Sub2', @destination_db = 'SubDB'  
  
exec sp_article_validation @publication = 'pub1', @article = 'art2',  
 @rowcount_only = 0, @full_or_fast = 0, @shutdown_agent = 0,  
 @subscription_level = 1  
  
commit tran  
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [レプリケートされたデータの検証](../../relational-databases/replication/validate-replicated-data.md)  
  
  
