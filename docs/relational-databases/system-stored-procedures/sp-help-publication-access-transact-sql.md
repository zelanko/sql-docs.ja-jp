---
title: sp_help_publication_access (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_help_publication_access
- sp_help_publication_access_TSQL
helpviewer_keywords:
- sp_help_publication_access
ms.assetid: 9408fa13-54a0-4cb1-8fb0-845e5536ef50
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: f4a8503a1c93283c2af8e6b4e2494cfdaff632b2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sphelppublicationaccess-transact-sql"></a>sp_help_publication_access (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリケーションに対して許可されたすべてのログインの一覧を返します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_publication_access [ @publication = ] 'publication'  
    [ , [ @return_granted = ] 'return_granted' ]   
    [ , [ @login = ] 'login' ]  
    [ , [ @initial_list = ] initial_list ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication=**] **'***publication***'**  
 アクセスするパブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@return_granted=**] **'***return_granted***'**  
 ログイン ID です。 *return_granted*は**ビット**、既定値は 1 です。 場合**0**が指定されていると[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証を使用すると、ディストリビューターではなく、パブリッシャー側で表示されるが、使用可能なログインが返されます。 場合**0**が指定されている Windows 認証を使用しでパブリッシャー アクセスが拒否以外にログインまたはディストリビューターが返されます。  
  
 [  **@login=**] **'***ログイン***'**  
 標準的なセキュリティ ログイン ID です。 *ログイン*は**sysname**、既定値は **%** です。  
  
 [  **@initial_list =**] *initial_list*  
 パブリケーションのアクセス権のあるすべてのメンバーを返すのか、新しいメンバーを一覧に追加する前にアクセスしたメンバーのみを返すのかを指定します。 *initial_list*は bit で、既定値は**0**します。  
  
 **1**のすべてのメンバーの情報を返します、 **sysadmin**現在のログインと同様に、パブリケーションが作成されたときに存在していたディストリビューターで有効なログインの固定サーバー ロール。  
  
 **0**のすべてのメンバーの情報を返します、 **sysadmin**しないユーザーに、パブリケーションで作成されたときも、すべてのユーザーのパブリケーション アクセス リストに存在していたディストリビューターで有効なログインを持つ固定サーバー ロール属している、 **sysadmin**固定サーバー ロール。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**Loginname**|**nvarchar (256)**|実際のログイン名です。|  
|**Isntname**|**int**|**0** = ログインは Windows ユーザーではありません。<br /><br /> **1** = ログインは Windows ユーザーです。|  
|**Isntgroup**|**int**|**0** = ログインは Windows グループではありません。<br /><br /> **1** = ログインは Windows グループです。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_help_publication_access**はあらゆる種類のレプリケーションで使用します。  
  
 ときに両方**Isntname**と**Isntgroup**結果セットは**0**、ログインがであると見なされます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_help_publication_access**です。  
  
## <a name="see-also"></a>参照  
 [sp_grant_publication_access &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-publication-access-transact-sql.md)   
 [sp_revoke_publication_access &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-publication-access-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
