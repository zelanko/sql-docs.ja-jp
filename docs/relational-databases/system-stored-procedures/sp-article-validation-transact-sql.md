---
title: sp_article_validation (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- sp_article_validation_TSQL
- sp_article_validation
helpviewer_keywords:
- sp_article_validation
ms.assetid: 44e7abcd-778c-4728-a03e-7e7e78d3ce22
caps.latest.revision: 30
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8bfe42f440f6311bf9a2badc368b8fd13811c91e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
 テーブルの行数のみを返す場合に指定します。 *type_of_check_requested*は**smallint**、既定値は**1**です。  
  
 場合**0**、行数を実行し、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 互換のチェックサム。  
  
 場合**1**行数のチェックのみを実行します。  
  
 場合**2**行数とバイナリ チェックサムを実行します。  
  
 [  **@full_or_fast=**] *full_or_fast*  
 行数の計算で使用する方法を指定します。 *full_or_fast*は**tinyint**、これらの値のいずれかを指定できます。  
  
|**値**|**Description**|  
|---------------|---------------------|  
|**0**|COUNT(*) を使用してフル カウントを実行します。|  
|**1**|高速カウントをから実行**sysindexes.rows**です。 行のカウント**sysindexes**実際のテーブル内の行のカウントより高速です。 ただし、 **sysindexes**遅れて、更新し、行数が正確でない場合があります。|  
|**2** (既定値)|最初に高速カウントを試み、条件高速カウントを実行します。 高速カウントに違いが見られる場合、フル カウントに戻されます。 場合*expected_rowcount*ストアド プロシージャの中を NULL 値を取得する、フル カウントが常に使用します。|  
  
 [  **@shutdown_agent=**] *shutdown_agent*  
 かどうか、ディストリビューション エージェント後をシャット ダウンすぐに検証の完了を指定します。 *shutdown_agent*は**ビット**、既定値は**0**します。 場合**0**、ディストリビューション エージェントがシャット ダウンできません。 場合**1**アーティクルが検証された後に、ディストリビューション エージェントがシャット ダウンします。  
  
 [  **@subscription_level=**] *subscription_level*  
 一部のサブスクライバーだけに検証を適用するかどうかを指定します。 *subscription_level*は**ビット**、既定値は**0**します。 場合**0**検証は、すべてのサブスクライバーに適用します。 場合**1**、検証は、サブスクライバーへの呼び出しで指定されたサブセットにのみ適用**sp_marksubscriptionvalidation**現在開いているトランザクションにします。  
  
 [  **@reserved=**]*予約済み*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ **@publisher**=] **'***パブリッシャー***'**  
 指定以外[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*検証を要求するときに使用しないで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_article_validation**トランザクション レプリケーションで使用します。  
  
 **sp_article_validation**検証の情報を指定したアーティクルで収集して、トランザクション ログに検証の要求を送信します。 ディストリビューション エージェントは、この要求を受け取ると、要求に含まれている検証の情報をサブスクライバー テーブルと比較します。 検証の結果は、レプリケーション モニターおよび [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの警告に表示されます。  
  
## <a name="permissions"></a>権限  
 検証するアーティクルが実行できる、ソース テーブルに対するすべての権限を選択を持つユーザー専用**sp_article_validation**です。  
  
## <a name="see-also"></a>参照  
 [レプリケートされたデータを検証します。](../../relational-databases/replication/validate-replicated-data.md)   
 [sp_marksubscriptionvalidation &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-marksubscriptionvalidation-transact-sql.md)   
 [sp_publication_validation &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md)   
 [sp_table_validation &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-validation-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
