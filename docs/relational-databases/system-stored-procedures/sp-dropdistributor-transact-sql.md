---
title: sp_dropdistributor (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
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
- sp_dropdistributor
- sp_dropdistributor_TSQL
helpviewer_keywords:
- sp_dropdistributor
ms.assetid: 0644032f-5ff0-4718-8dde-321bc9967a03
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: ff542116aea50e514339e11fea5a73f5baa590a2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spdropdistributor-transact-sql"></a>sp_dropdistributor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ディストリビューターをアンインストールします。 このストアド プロシージャは、ディストリビューター側でディストリビューション データベースを除くすべてのデータベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropdistributor [ [ @no_checks= ] no_checks ]   
    [ , [ @ignore_distributor= ] ignore_distributor ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@no_checks=**] *no_checks*  
 ディストリビューターを削除する前に、従属オブジェクトを確認するかどうかを指定します。 *no_checks*は**ビット**、既定値は 0 です。  
  
 場合**0**、 **sp_dropdistributor**をディストリビューター以外のすべてのパブリッシングおよびディストリビューション オブジェクトが破棄されたかどうかを確認します。  
  
 場合**1**、 **sp_dropdistributor**ディストリビューターをアンインストールする前にすべてのパブリッシングおよびディストリビューション オブジェクトを削除します。  
  
 [  **@ignore_distributor=**] *ignore_distributor*  
 ディストリビューターに接続せずに、このストアド プロシージャを実行するかどうかを指定します。 *ignore_distributor*は**ビット**、既定値は**0**します。  
  
 場合**0**、 **sp_dropdistributor**ディストリビューターに接続して、すべてのレプリケーション オブジェクトを削除します。 場合**sp_dropdistributor**ストアド プロシージャが失敗する、ディストリビューターに接続することはありません。  
  
 場合**1**ディストリビューターに接続が確立されませんし、レプリケーション オブジェクトは削除されません。 これが使用されるのは、ディストリビューターがアンインストールされているか、完全にオフラインになっている場合です。 ディストリビューターでのパブリッシャーに関連するオブジェクトは、後でディストリビューターが再インストールされるまで削除されません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_dropdistributor**はあらゆる種類のレプリケーションで使用します。  
  
 サーバーで、その他のパブリッシャーまたはディストリビューション オブジェクトが存在しない場合**sp_dropdistributor**失敗しない限り、 **@no_checks**に設定されている**1**です。  
  
 このストアド プロシージャを実行することによって、ディストリビューション データベースの削除後に実行する必要があります**sp_dropdistributiondb**です。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_DropDistPub](../../relational-databases/replication/codesnippet/tsql/sp-dropdistributor-trans_1.sql)]  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_dropdistributor**です。  
  
## <a name="see-also"></a>参照  
 [パブリッシングおよびディストリビューションの無効化](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [sp_adddistributor &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md)   
 [sp_changedistributor_property &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
