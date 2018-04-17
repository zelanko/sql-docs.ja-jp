---
title: sp_redirect_publisher (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
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
- sp_redirect_publisher_TSQL
- sp_redirect_publisher
helpviewer_keywords:
- sp_redirect_publisher
ms.assetid: af45e2b2-57fb-4bcd-a58b-e61401fb3b26
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7b3d858bdc28028750f481616f908239b7290473
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spredirectpublisher-transact-sql"></a>sp_redirect_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  既存のパブリッシャーとデータベースのペアのリダイレクトされたパブリッシャーを指定します。 パブリッシャー データベースに属する場合、Always On 可用性グループ、可用性グループに関連付けられている可用性グループ リスナー名は、リダイレクトされたパブリッシャーです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_redirect_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name'   
    [ , [ @redirected_publisher = ] 'new_publisher' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@original_publisher** =] **'***original_publisher***'**  
 インスタンスの名前[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースを最初に発行します。 *original_publisher*は**sysname**、既定値はありません。  
  
 [ **@publisher_db** =] **'***publisher_db***'**  
 パブリッシュされるデータベースの名前。 *publisher_db*は**sysname**、既定値はありません。  
  
 [ **@redirected_publisher** =] **'***redirected_publisher***'**  
 新しいパブリッシャーになる、可用性グループに関連付けられている可用性グループ リスナーの名前。 *redirected_publisher*は**sysname**、既定値はありません。 可用性グループ リスナーが既定以外のポートに対して構成されている場合は、`'Listenername,51433'` のように、リスナー名と共にポート番号を指定します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 **sp_redirect_publisher**がレプリケーション パブリッシャーを可用性グループのリスナーと、パブリッシャー/データベース ペアを関連付けることによって Always On 可用性グループの現在のプライマリにリダイレクトを許可するために使用します。 実行**sp_redirect_publisher**パブリッシュされたデータベースを含む可用性グループに対して AG リスナーを構成した後です。  
  
 元のパブリッシャーでパブリケーション データベースを可用性グループのプライマリ レプリカから削除する場合は、実行**sp_redirect_publisher**の値を指定せず、 *@redirected_publisher*パブリッシャー/データベース ペアのリダイレクトを削除するパラメーターです。 パブリッシャーのリダイレクトの詳細についてを参照してください[AlwaysOn パブリケーション データベースのメンテナンス&#40;SQL Server&#41;](../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md)です。  
  
## <a name="permissions"></a>権限  
 呼び出し元必要がありますいずれかのメンバーである、 **sysadmin**固定サーバー ロール、 **db_owner**定義済みパブリケーションのパブリケーション アクセス リストのメンバーまたはディストリビューション データベースの固定データベース ロールパブリッシャー データベースと関連付けられています。  
  
## <a name="see-also"></a>参照  
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_validate_redirected_publisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)   
 [sp_get_redirected_publisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
