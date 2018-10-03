---
title: sp_article_validation (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_article_validation_TSQL
- sp_article_validation
helpviewer_keywords:
- sp_article_validation
ms.assetid: 44e7abcd-778c-4728-a03e-7e7e78d3ce22
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 921ddeb18eff52731b78a56c0a2c056575572b05
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47648700"
---
# <a name="sparticlevalidation-transact-sql"></a>sp_article_validation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたアーティクルに対する検証の要求を開始します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて、およびサブスクライバー側でサブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_article_validation [ @publication = ] 'publication'  
    [ , [ @article = ] 'article' ]  
    [ , [ @rowcount_only = ] type_of_check_requested ]  
    [ , [ @full_or_fast = ] full_or_fast ]  
    [ , [ @shutdown_agent = ] shutdown_agent ]  
    [ , [ @subscription_level = ] subscription_level ]  
    [ , [ @reserved = ] reserved ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication=**] **'***publication***'**  
 アーティクルが存在するパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@article=**] **'***記事***'**  
 検証するアーティクルの名前を指定します。 *記事*は**sysname**、既定値はありません。  
  
 [  **@rowcount_only=**] *type_of_check_requested*  
 テーブルの行数のみを返す場合に指定します。 *type_of_check_requested*は**smallint**、既定値は**1**します。  
  
 場合**0**、行数を実行し、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 互換のチェックサム。  
  
 場合**1**、行数チェックのみを実行します。  
  
 場合**2**行数とバイナリ チェックサムを実行します。  
  
 [  **@full_or_fast=**] *full_or_fast*  
 行数の計算で使用する方法を指定します。 *full_or_fast*は**tinyint**、これらの値のいずれかを指定できます。  
  
|**[値]**|**[説明]**|  
|---------------|---------------------|  
|**0**|COUNT(*) を使用してフル カウントを実行します。|  
|**1**|高速カウントを実行します。 **sysindexes.rows**します。 行のカウント**sysindexes**は実際のテーブル内の行のカウントよりも高速です。 ただし、 **sysindexes**の更新は時間、および行カウントが正しくない可能性があります。|  
|**2** (既定値)|最初に高速カウントを試み、条件高速カウントを実行します。 高速カウントに違いが見られる場合、フル カウントに戻されます。 場合*expected_rowcount*ストアド プロシージャの中を NULL 値を取得する、フル カウント(\*) が常に使用します。|  
  
 [  **@shutdown_agent=**] *shutdown_agent*  
 検証の完了後、ディストリビューション エージェント、直ちにシャットかどうかを指定します。 *shutdown_agent*は**ビット**、既定値は**0**します。 場合**0**、ディストリビューション エージェントがシャット ダウンされません。 場合**1**アーティクルの検証後にディストリビューション エージェントがシャット ダウンします。  
  
 [  **@subscription_level=**] *subscription_level*  
 一部のサブスクライバーだけに検証を適用するかどうかを指定します。 *subscription_level*は**ビット**、既定値は**0**します。 場合**0**、すべてのサブスクライバーに検証が適用されます。 場合**1**、検証は、サブスクライバーへの呼び出しで指定されたサブセットにのみ適用**sp_marksubscriptionvalidation**で現在開いているトランザクションです。  
  
 [  **@reserved=**]*予約済み*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ **@publisher**=] **'***パブリッシャー***'**  
 以外を指定[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*で検証を要求するときに使用されません、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_article_validation**はトランザクション レプリケーションで使用します。  
  
 **sp_article_validation**検証の情報を指定したアーティクルで収集して、トランザクション ログへの検証要求を投稿します。 ディストリビューション エージェントは、この要求を受け取ると、要求に含まれている検証の情報をサブスクライバー テーブルと比較します。 検証の結果は、レプリケーション モニターおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの警告に表示されます。  
  
## <a name="permissions"></a>アクセス許可  
 検証するアーティクルが実行できる、ソース テーブルですべてのアクセス許可を選択を持つユーザーのみ**sp_article_validation**します。  
  
## <a name="see-also"></a>参照  
 [レプリケートされたデータを検証します。](../../relational-databases/replication/validate-replicated-data.md)   
 [sp_marksubscriptionvalidation &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-marksubscriptionvalidation-transact-sql.md)   
 [sp_publication_validation &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md)   
 [sp_table_validation &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-validation-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
