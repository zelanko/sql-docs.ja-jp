---
title: sp_replicationdboption (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_replicationdboption_TSQL
- sp_replicationdboption
helpviewer_keywords:
- sp_replicationdboption
ms.assetid: d021864e-3f21-4d1a-89df-6c1086f753bf
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: be7d8869c2f1b1453eab4efcf3c6145b6dafea9d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47781687"
---
# <a name="spreplicationdboption-transact-sql"></a>sp_replicationdboption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したデータベースのレプリケーション データベース オプションを設定します。 このストアド プロシージャは、任意のデータベース上のパブリッシャー側またはサブスクライバー側で実行されます。  
  
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
 [**@dbname=**] **'***dbname***'**  
 レプリケーション データベース オプションを設定するデータベースを指定します。 *db_name*は**sysname**、既定値はありません。  
  
 [**@optname=**] **'***optname***'**  
 有効または無効にするレプリケーション データベース オプションを指定します。 *optname*は**sysname**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**マージ パブリッシュします。**|データベースは、マージ パブリケーションで使用できます。|  
|**発行**|データベースは、他の種類のパブリケーションで使用できます。|  
|**サブスクライブ**|データベースは、サブスクリプション データベースです。|  
|**バックアップと同期します。**|データベースが連携バックアップに対して有効になっています。 詳細については、次を参照してください。[トランザクション レプリケーションの連携バックアップの有効化&#40;レプリケーション TRANSACT-SQL プログラミング&#41;](../../relational-databases/replication/administration/enable-coordinated-backups-for-transactional-replication.md)します。|  
  
 [  **@value=**] **'***値***'**  
 指定したデータベース オプションを有効にするか無効にするかを指定します。 *値*は**sysname**、でき、 **true**または**false**します。 この値が**false**と*optname*は**マージ パブリッシュ**、マージ パブリッシュされたデータベースへのサブスクリプションが削除されます。  
  
 [  **@ignore_distributor=**] *ignore_distributor*  
 ディストリビューターに接続せずに、このストアド プロシージャを実行するかどうかを指定します。 *ignore_distributor*は**ビット**、既定値は**0**、ディストリビューターに接続して、パブリッシング データベースの新しい状態を反映します。 値**1**のみ指定してください、ディストリビューターがアクセスできるかどうかと**sp_replicationdboption**パブリッシングを無効にされています。  
  
 [  **@from_scripting=**] *from_scripting*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_replicationdboption**はスナップショット レプリケーション、トランザクション レプリケーション、およびマージ レプリケーションで使用します。  
  
 このプロシージャでは、指定したオプションに従って、特定のレプリケーション システム テーブル、セキュリティ アカウントなどが作成または削除されます。 対応するカテゴリ ビットがセット、 **master.sysdatabases**システム テーブルと必要なシステム テーブルを作成します。  
  
 パブリッシングを無効にするには、パブリケーション データベースがオンラインであることが必要です。 パブリケーション データベースにデータベース スナップショットが存在する場合は、パブリッシングを無効にする前に削除する必要があります。 データベース スナップショットは、データベースの読み取り専用のオフライン コピーであり、レプリケーション スナップショットには関係していません。 詳細については、「[データベース スナップショット &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)」を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_replicationdboption**します。  
  
## <a name="see-also"></a>参照  
 [パブリッシングとディストリビューションの構成](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [パブリケーションを削除します](../../relational-databases/replication/publish/delete-a-publication.md)   
 [パブリッシングおよびディストリビューションの無効化](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [sys.sysdatabases &#40;TRANSACT-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysdatabases-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
