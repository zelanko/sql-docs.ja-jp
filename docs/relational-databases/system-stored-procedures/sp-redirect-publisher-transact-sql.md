---
title: sp_redirect_publisher (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_redirect_publisher_TSQL
- sp_redirect_publisher
helpviewer_keywords:
- sp_redirect_publisher
ms.assetid: af45e2b2-57fb-4bcd-a58b-e61401fb3b26
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6062522ca6c5c3a311ba2f2c796f791c47e874ab
ms.sourcegitcommit: c426c7ef99ffaa9e91a93ef653cd6bf3bfd42132
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252117"
---
# <a name="sp_redirect_publisher-transact-sql"></a>sp_redirect_publisher (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  既存のパブリッシャー/データベースペアのリダイレクトされたパブリッシャーを指定します。 パブリッシャーデータベースが Always On 可用性グループに属している場合、リダイレクトされたパブリッシャーは可用性グループに関連付けられている可用性グループリスナー名になります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_redirect_publisher   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name'   
    [ , [ @redirected_publisher = ] 'new_publisher' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @original_publisher = ] 'original_publisher'` は、データベースを最初にパブリッシュした @no__t のインスタンスの名前です。 *original_publisher*は**sysname**,、既定値はありません。  
  
`[ @publisher_db = ] 'publisher_db'` パブリッシュするデータベースの名前。 *publisher_db* は **sysname** 、既定値はありません。  
  
`[ @redirected_publisher = ] 'redirected_publisher'` 新しいパブリッシャーになる可用性グループに関連付けられている可用性グループリスナーの名前。 *redirected_publisher*は**sysname**,、既定値はありません。 可用性グループ リスナーが既定以外のポートに対して構成されている場合は、`'Listenername,51433'` のように、リスナー名と共にポート番号を指定します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>コメント  
 **sp_redirect_publisher**は、パブリッシャー/データベースペアを可用性グループのリスナーに関連付けることによって、レプリケーションパブリッシャーを Always On 可用性グループの現在のプライマリにリダイレクトできるようにするために使用されます。 パブリッシュされたデータベースを含む可用性グループに対して AG リスナーが構成された後に、 **sp_redirect_publisher**を実行します。  
  
 元のパブリッシャーのパブリケーションデータベースが、プライマリレプリカの可用性グループから削除されている場合は、sp_redirect_publisher パラメーターの *@no__t*値を指定せずにを実行して、パブリッシャー/データベースペアのリダイレクト。 の場合のパブリッシャーのリダイレクトの詳細については、「 [AlwaysOn &#40;パブリケーション&#41;データベースのメンテナンス SQL Server](../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 呼び出し元は、 **sysadmin**固定サーバーロールのメンバー、ディストリビューションデータベースの**db_owner**固定データベースロールのメンバーであるか、パブリッシャーデータベースに関連付けられている定義済みパブリケーションのパブリケーションアクセスリストのメンバーである必要があります。  
  
## <a name="see-also"></a>関連項目  
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [sp_validate_redirected_publisher &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)   
 [sp_get_redirected_publisher &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [sp_validate_replica_hosts_as_publishers &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-validate-replica-hosts-as-publishers-transact-sql.md)  
  
  
