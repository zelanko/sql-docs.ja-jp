---
title: sp_replcmds (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_replcmds_TSQL
- sp_replcmds
helpviewer_keywords:
- sp_replcmds
ms.assetid: 7e932f80-cc6e-4109-8db4-2b7c8828df73
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 00fec83a709b1c3bfba352663784b5018134769d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47783496"
---
# <a name="spreplcmds-transact-sql"></a>sp_replcmds (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  レプリケーションするようマークが付けられたトランザクションのコマンドを返します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
> [!IMPORTANT]  
>  **Sp_replcmds**プロシージャがレプリケーションに関する問題のトラブルシューティングにのみ実行する必要があります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_replcmds [ @maxtrans = ] maxtrans  
```  
  
## <a name="arguments"></a>引数  
 [  **@maxtrans=**] *maxtrans*  
 情報を返すトランザクションの数です。 *maxtrans*は**int**、既定値は**1**、ディストリビューション待ちの次のトランザクションを指定します。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**アーティクル id**|**int**|アーティクルの ID。|  
|**partial_command**|**bit**|これが部分的なコマンドかどうかを示します。|  
|**command**|**varbinary(1024)**|コマンドの値。|  
|**xactid**|**binary(10)**|トランザクション id。|  
|**xact_seqno**|**varbinary(16)**|トランザクション シーケンス番号です。|  
|**publication_id**|**int**|パブリケーションの ID。|  
|**command_id**|**int**|内のコマンドの ID [MSrepl_commands](../../relational-databases/system-tables/msrepl-commands-transact-sql.md)します。|  
|**command_type**|**int**|コマンドの種類です。|  
|**originator_srvname**|**sysname**|トランザクションが発生したサーバーです。|  
|**originator_db**|**sysname**|トランザクションが発生したデータベースです。|  
|**pkHash**|**int**|内部使用のみです。|  
|**originator_publication_id**|**int**|トランザクションが発生したパブリケーションの ID です。|  
|**originator_db_version**|**int**|トランザクションが発生したデータベースのバージョンです。|  
|**originator_lsn**|**varbinary(16)**|発生元パブリケーションでのコマンドのログ シーケンス番号 (LSN) を識別します。|  
  
## <a name="remarks"></a>コメント  
 **sp_replcmds**トランザクション レプリケーションでログ読み取りプロセスによって使用されます。  
  
 レプリケーション処理を実行する最初のクライアント**sp_replcmds**ログ リーダーとして特定のデータベースでします。  
  
 このプロシージャは、所有者限定テーブルまたはテーブル名が限定されていないテーブル (既定値) に対するコマンドを生成します。 限定されたテーブル名を追加することにより、あるデータベースの特定のユーザーが所有するテーブルから、別のデータベースで同じユーザーが所有するテーブルにデータのレプリケーションが可能になります。  
  
> [!NOTE]  
>  レプリケーション元データベースのテーブル名は、所有者名により限定されるので、レプリケーション先データベースのテーブルの所有者も同じ所有者名である必要があります。  
  
 クライアントを実行しようとした**sp_replcmds**同じデータベース内で最初のクライアントが切断されるまでにエラー 18752 を受け取ります。 別のクライアントを実行できる最初のクライアントが切断した後**sp_replcmds**、され、新しいログ リーダーになります。  
  
 両方に警告メッセージ番号 18759 が追加された、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラー ログと[!INCLUDE[msCoName](../../includes/msconame-md.md)]Windows アプリケーション ログ**sp_replcmds**テキスト ポインターができなかったため、テキスト コマンドをレプリケートすることはできません同じトランザクションで取得します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_replcmds**します。  
  
## <a name="see-also"></a>参照  
 [エラー メッセージ](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [sp_repldone &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
