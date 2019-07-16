---
title: sp_help_publication_access (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_help_publication_access
- sp_help_publication_access_TSQL
helpviewer_keywords:
- sp_help_publication_access
ms.assetid: 9408fa13-54a0-4cb1-8fb0-845e5536ef50
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8af56ae768ca883e22d7c9e18150e75025086d63
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085262"
---
# <a name="sphelppublicationaccess-transact-sql"></a>sp_help_publication_access (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリケーションのすべてのログインを許可した権限の一覧を返します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_publication_access [ @publication = ] 'publication'  
    [ , [ @return_granted = ] 'return_granted' ]   
    [ , [ @login = ] 'login' ]  
    [ , [ @initial_list = ] initial_list ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'` アクセスするパブリケーションの名前です。 *パブリケーション* は **sysname** 、既定値はありません。  
  
`[ @return_granted = ] 'return_granted'` ログイン ID です。 *return_granted*は**ビット**、既定値は 1 です。 場合**0**を指定し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証を使用すると、ディストリビューターではなく、パブリッシャー側で表示されるが、使用可能なログインが返されます。 場合**0**が指定されて Windows 認証を使用しでパブリッシャー アクセスが拒否しないログインまたはディストリビューターが返されます。  
  
`[ @login = ] 'login'` 標準的なセキュリティ ログイン ID です。 *ログイン*は**sysname**、既定値は **%** します。  
  
`[ @initial_list = ] initial_list` パブリケーションのアクセス権または新しいメンバーが一覧に追加された前にアクセスしたものだけを持つすべてのメンバーを返すかどうかを指定します。 *initial_list*は bit で、既定値は、 **0**します。  
  
 **1**のすべてのメンバーの情報を返します、 **sysadmin**現在のログインと同様に、パブリケーションを作成したときに存在していたディストリビューターでの有効なログインの固定サーバー ロール。  
  
 **0**のすべてのメンバーの情報を返します、 **sysadmin**しないユーザーには、パブリケーションの作成時にもすべてのユーザー、パブリケーション アクセス リストに存在していたディストリビューターでの有効なログインを固定サーバー ロール属している、 **sysadmin**固定サーバー ロール。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**Loginname**|**nvarchar (256)**|実際のログイン名です。|  
|**isntname**|**int**|**0** = ログインは Windows ユーザーではありません。<br /><br /> **1** = ログインは Windows ユーザーです。|  
|**isntgroup**|**int**|**0** = ログインは Windows グループではありません。<br /><br /> **1** = ログインは Windows グループ。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_help_publication_access**はあらゆる種類のレプリケーションで使用します。  
  
 ときに両方**Isntname**と**Isntgroup**結果セットは**0**、ログインがあると見なされます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_help_publication_access**します。  
  
## <a name="see-also"></a>関連項目  
 [sp_grant_publication_access &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql.md)   
 [sp_revoke_publication_access &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
