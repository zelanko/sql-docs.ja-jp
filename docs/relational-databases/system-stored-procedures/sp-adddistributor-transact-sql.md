---
title: sp_adddistributor (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_adddistributor
- sp_adddistributor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_adddistributor
ms.assetid: 35415502-68d0-40f6-993c-180e50004f1e
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8cf36a02d81b8732d80beb7c97d025a74138cd43
ms.sourcegitcommit: aeb2273d779930e76b3e907ec03397eab0866494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67716727"
---
# <a name="spadddistributor-transact-sql"></a>sp_adddistributor (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  エントリを作成、 [sys.sysservers](../../relational-databases/system-compatibility-views/sys-sysservers-transact-sql.md)テーブル (が存在しない) 場合は、ディストリビューターとしてサーバー エントリをマークし、プロパティ情報を格納します。 このストアド プロシージャは、master データベースでディストリビューターに登録し、サーバーをディストリビューターとしてのマークで実行されます。 リモート ディストリビューターの場合、このストアド プロシージャは、master データベースからパブリッシャー側でも実行され、リモート ディストリビューターを登録します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_adddistributor [ @distributor= ] 'distributor'   
    [ , [ @heartbeat_interval= ] heartbeat_interval ]   
    [ , [ @password= ] 'password' ]   
    [ , [ @from_scripting= ] from_scripting ]  
```  
  
## <a name="arguments"></a>引数  
`[ @distributor = ] 'distributor'` ディストリビューション サーバー名です。 *ディストリビューター*は**sysname**、既定値はありません。 このパラメーターは、リモート ディストリビューターを設定する場合にのみ使用します。 ディストリビューターのプロパティ エントリを追加します、 **msdb.MSdistributor**テーブル。  
  
`[ @heartbeat_interval = ] heartbeat_interval` エージェントは、進行状況メッセージをログ記録しなくてもよい分の最大数です。 *heartbeat_interval*は**int**、既定値は 10 分です。 実行されているレプリケーション エージェントの状態を確認するには、この間隔で実行されている SQL Server エージェント ジョブが作成されます。  
  
`[ @password = ] 'password']` パスワード、 **distributor_admin**ログインします。 *パスワード*は**sysname**、既定値は NULL です。 NULL または空の文字列にパスワードをリセットかどうか、ランダムな値。 パスワードは最初のリモート ディストリビューターを追加するときに構成する必要があります。 **distributor_admin**ログインと*パスワード*に使用されるリンク サーバー エントリ用の保存されて、*ディストリビューター*ローカル接続を含む、RPC 接続します。 場合*ディストリビューター*がローカルでのパスワードを**distributor_admin**が新しい値に設定します。 同じ値をリモート ディストリビューターとパブリッシャーの場合、*パスワード*を実行するときに指定する必要があります**sp_adddistributor**パブリッシャーとディストリビューターの両方でします。 [sp_changedistributor_password](../../relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql.md)ディストリビューターのパスワードを変更するために使用できます。  
  
> [!IMPORTANT]  
>  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
`[ @from_scripting = ] from_scripting` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_adddistributor**はスナップショット レプリケーション、トランザクション レプリケーション、およびマージ レプリケーションで使用します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#AddDistPub](../../relational-databases/replication/codesnippet/tsql/sp-adddistributor-transa_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_adddistributor**します。  
  
## <a name="see-also"></a>関連項目  
 [パブリッシングとディストリビューションの構成](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [sp_changedistributor_property &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql.md)   
 [sp_dropdistributor &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [[ディストリビューションの構成]](../../relational-databases/replication/configure-distribution.md)  
  
  
