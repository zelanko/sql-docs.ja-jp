---
title: sp_replicationdboption (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replicationdboption_TSQL
- sp_replicationdboption
helpviewer_keywords:
- sp_replicationdboption
ms.assetid: d021864e-3f21-4d1a-89df-6c1086f753bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b45da78b0a79130cbbbd6c39bee07f237de2ef89
ms.sourcegitcommit: dacf6c57f6a2e3cf2005f3268116f3c609639905
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70878728"
---
# <a name="sp_replicationdboption-transact-sql"></a>sp_replicationdboption (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  指定したデータベースのレプリケーション データベース オプションを設定します。 このストアドプロシージャは、任意のデータベースのパブリッシャーまたはサブスクライバーで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_replicationdboption [ @dbname= ] 'db_name'   
        , [ @optname= ] 'optname'   
        , [ @value= ] 'value'   
    [ , [ @ignore_distributor= ] ignore_distributor ]  
    [ , [ @from_scripting = ] from_scripting ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@dbname=** ] **'***dbname***'**  
 レプリケーションデータベースオプションを設定するデータベースを指定します。 *db_name*は**sysname**,、既定値はありません。  
  
 [ **@optname=** ] **'***optname***'**  
 有効または無効にするレプリケーションデータベースオプションを指定します。 *optname*は**sysname**で、次のいずれかの値を指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**マージ発行**|データベースは、マージ パブリケーションで使用できます。|  
|**投稿**|データベースは、他の種類のパブリケーションで使用できます。|  
|**web**|データベースはサブスクリプションデータベースです。|  
|**バックアップとの同期**|データベースは、連携バックアップに対して有効になっています。 詳細については、「[トランザクション&#40;レプリケーションレプリケーションでの連携バックアップの有効化&#41;transact-sql プログラミング](../../relational-databases/replication/administration/enable-coordinated-backups-for-transactional-replication.md)」を参照してください。|  
  
`[ @value = ] 'value'`指定したレプリケーションデータベースオプションを有効にするか無効にするかを指定します。 *値*は**sysname**で、 **true**または**false**を指定できます。 この値が**false**で、 *optname*が**merge publish**の場合、マージパブリッシュされたデータベースに対するサブスクリプションも削除されます。  
  
`[ @ignore_distributor = ] ignore_distributor`ディストリビューターに接続せずにこのストアドプロシージャを実行するかどうかを示します。 *ignore_distributor*のデータ型は**bit**で、既定値は**0**です。これは、ディストリビューターがパブリッシングデータベースの新しい状態に接続され、更新されることを意味します。 値**1**は、ディストリビューターにアクセスできない場合にのみ指定し、 **sp_replicationdboption**を使用してパブリッシングを無効にする必要があります。  
  
`[ @from_scripting = ] from_scripting` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_replicationdboption**は、スナップショットレプリケーション、トランザクションレプリケーション、およびマージレプリケーションで使用します。  
  
 このプロシージャでは、指定したオプションに従って、特定のレプリケーション システム テーブル、セキュリティ アカウントなどが作成または削除されます。 Is_published システムテーブルの対応する (transacational またはスナップショットレプリケーション)、 **is_merge_published** (マージレプリケーション)、または**is_distributor**ビットを設定し、必要なシステムを作成し**ます。** テーブル.  
  
 パブリッシングを無効にするには、パブリケーションデータベースがオンラインである必要があります。 パブリケーションデータベースのデータベーススナップショットが存在する場合は、パブリッシングを無効にする前にデータベーススナップショットを削除する必要があります。 データベーススナップショットは、データベースの読み取り専用のオフラインコピーであり、レプリケーションスナップショットに関連付けられていません。 詳細については、「[データベース スナップショット &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_replicationdboption**を実行できるのは、 **sysadmin**固定サーバーロールのメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [パブリッシングとディストリビューションの構成](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [パブリケーションを削除する](../../relational-databases/replication/publish/delete-a-publication.md)   
 [パブリッシングおよびディストリビューションの無効化](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
