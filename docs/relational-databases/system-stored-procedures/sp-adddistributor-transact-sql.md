---
title: "sp_adddistributor (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_adddistributor
- sp_adddistributor_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_adddistributor
ms.assetid: 35415502-68d0-40f6-993c-180e50004f1e
caps.latest.revision: "35"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bfdf3aa6cbd888385f00afad8594cb6427ac071b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spadddistributor-transact-sql"></a>sp_adddistributor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  内のエントリを作成、 [sys.sysservers](../../relational-databases/system-compatibility-views/sys-sysservers-transact-sql.md)テーブル (が存在しない) 場合は、ディストリビューターとしてサーバー エントリをマークし、プロパティ情報を格納します。 このストアド プロシージャは、ディストリビューター側で master データベースについて実行され、サーバーをディストリビューターとして登録し、サーバーにディストリビューターのマークを付けます。 リモート ディストリビューターの場合、このストアド プロシージャは、master データベースからパブリッシャー側でも実行され、リモート ディストリビューターを登録します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_adddistributor [ @distributor= ] 'distributor'   
    [ , [ @heartbeat_interval= ] heartbeat_interval ]   
    [ , [ @password= ] 'password' ]   
    [ , [ @from_scripting= ] from_scripting ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@distributor=**] **'***ディストリビューター***'**  
 ディストリビューション サーバー名です。 *ディストリビューター*は**sysname**、既定値はありません。 このパラメーターは、リモート ディストリビューターを設定する場合にのみ使用します。 ディストリビューターのプロパティのエントリを追加、 **msdb.MSdistributor**テーブル。  
  
 [  **@heartbeat_interval=**] *heartbeat_interval*  
 エージェントが進捗状況を示すメッセージをログに記録しなくてもよい最大時間を分単位で示します。 *heartbeat_interval*は**int**、10 分間の既定値です。 この間隔で実行され、実行中のレプリケーション エージェントの状態を確認する SQL Server エージェント ジョブが作成されます。  
  
 [  **@password=**] **'***パスワード***'**]  
 パスワードを指定します、 **distributor_admin**ログインします。 *パスワード*は**sysname**、既定値は NULL です。 NULL または空の文字列である場合、パスワードはランダムな値に再設定されます。 パスワードは最初のリモート ディストリビューターを追加するときに構成する必要があります。 **distributor_admin**ログインと*パスワード*使用されるリンク サーバー エントリ用の保存されて、*ディストリビューター*ローカル接続を含む、RPC 接続します。 場合*ディストリビューター*がローカルでのパスワード**distributor_admin**が新しい値に設定します。 リモート ディストリビューターを持つパブリッシャーは、同じ値を*パスワード*を実行するときに指定する必要があります**sp_adddistributor**パブリッシャーとディストリビューターの両方でします。 [sp_changedistributor_password](../../relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql.md)ディストリビューターのパスワードを変更するために使用できます。  
  
> [!IMPORTANT]  
>  可能であれば、実行時、ユーザーに対してセキュリティ資格情報の入力を要求します。 スクリプト ファイルに資格情報を格納する必要がある場合は、不正アクセスを防ぐために、ファイルを保護します。  
  
 [  **@from_scripting=** ] *from_scripting*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_adddistributor**はスナップショット レプリケーション、トランザクション レプリケーション、およびマージ レプリケーションで使用します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#AddDistPub](../../relational-databases/replication/codesnippet/tsql/sp-adddistributor-transa_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_adddistributor**です。  
  
## <a name="see-also"></a>参照  
 [パブリッシングとディストリビューションの構成](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [sp_changedistributor_property &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql.md)   
 [sp_dropdistributor &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [ディストリビューションの構成](../../relational-databases/replication/configure-distribution.md)  
  
  
