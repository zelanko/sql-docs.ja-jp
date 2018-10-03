---
title: sp_redirect_publisher (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_redirect_publisher_TSQL
- sp_redirect_publisher
helpviewer_keywords:
- sp_redirect_publisher
ms.assetid: af45e2b2-57fb-4bcd-a58b-e61401fb3b26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d2a6ecf88b7b41929644b78e04544e47f5f98b61
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47718770"
---
# <a name="spredirectpublisher-transact-sql"></a>sp_redirect_publisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  既存のパブリッシャーとデータベースのペアのリダイレクトされたパブリッシャーを指定します。 パブリッシャー データベースが Always On 可用性グループに所属している場合、リダイレクトされたパブリッシャーは可用性グループに関連付けられている可用性グループ リスナー名にします。  
  
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
  
## <a name="remarks"></a>コメント  
 **sp_redirect_publisher**パブリッシャー/データベース ペアを可用性グループのリスナーに関連付けることによって、Always On 可用性グループの現在のプライマリにリダイレクトされるレプリケーションのパブリッシャーを許可するために使用します。 実行**sp_redirect_publisher**パブリッシュされたデータベースを含む可用性グループに対して AG リスナーを構成した後。  
  
 元のパブリッシャーでパブリケーション データベースを可用性グループのプライマリ レプリカから削除する場合は、実行**sp_redirect_publisher**の値を指定せず、 *@redirected_publisher*パブリッシャー/データベース ペアのリダイレクトを削除するパラメーター。 パブリッシャーのリダイレクトの詳細についてを参照してください[AlwaysOn パブリケーション データベースのメンテナンス&#40;SQL Server&#41;](../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md)します。  
  
## <a name="permissions"></a>アクセス許可  
 呼び出し元する必要がありますいずれかのメンバーである、 **sysadmin**固定サーバー ロール、 **db_owner**固定データベース ロールには、ディストリビューション データベースまたは定義済みパブリケーションのパブリケーション アクセス リストのメンバーパブリッシャー データベースと関連付けられています。  
  
## <a name="see-also"></a>参照  
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_validate_redirected_publisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)   
 [sp_get_redirected_publisher &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
