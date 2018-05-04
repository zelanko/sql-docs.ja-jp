---
title: sp_showpendingchanges (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
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
- sp_showpendingchanges
- sp_showpendingchanges_TSQL
helpviewer_keywords:
- sp_showpendingchanges
ms.assetid: 8013a792-639d-4550-b262-e65d30f9d291
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 9b05623d177bac68c5aafe0b4ac9df2931b27732
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spshowpendingchanges-transact-sql"></a>sp_showpendingchanges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  レプリケート待ちの変更を示す結果セットを返します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて、およびサブスクライバー側でサブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
> [!NOTE]  
>  このプロシージャでは、変更の概数と、その変更に関係する行が提供されます。 たとえば、プロシージャは、パブリッシャーまたはサブスクライバーから情報を取得しますが、同時に両方の情報を取得しません。 他のノードに格納されている情報によって、同期する一連の変更はプロシージャで推定されるよりも少なくなる可能性があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_showpendingchanges [ [ @destination_server = ] 'destination_server' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article']  
    [ , [ @show_rows = ] show_rows]  
```  
  
## <a name="arguments"></a>引数  
 [ @destination_server **=** ] **'***destination_server***'**  
 レプリケートされた変更が適用されるサーバーの名前を指定します。 *destination_server*は**sysname**既定値は NULL です。  
  
 [ @publication **=** ] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**既定値は NULL です。 ときに*パブリケーション*を指定すると、結果は、指定されたパブリケーションのみに制限されています。  
  
 [ @article **=** ] **'***記事***'**  
 アーティクルの名前を指定します。 *記事*は**sysname**既定値は NULL です。 ときに*記事*を指定すると、結果は、指定したアーティクルのみに制限されています。  
  
 [ @show_rows **=** ] *show_rows*  
 結果セットが、保留中の変更、既定値はに関するより具体的な情報を格納するかどうかを示す**0**します。 値の場合**1**を指定すると、結果セットには、列 is_delete 列と rowguid が含まれています。  
  
## <a name="result-set"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|destination_server|**sysname**|変更がレプリケートされているサーバーの名前です。|  
|pub_name|**sysname**|パブリケーションの名前を指定します。|  
|destination_db_name|**sysname**|変更がレプリケートされているデータベースの名前です。|  
|is_dest_subscriber|**bit**|変更がサブスクライバーにレプリケートされていることを示します。 値**1**変更がサブスクライバーにレプリケートされることを示します。 **0**変更がパブリッシャーにレプリケートされていることを意味します。|  
|article_name|**sysname**|変更が行われたテーブルのアーティクルの名前です。|  
|pending_deletes|**int**|レプリケートされるのを待機している削除の数です。|  
|pending_ins_and_upd|**int**|レプリケートされるのを待機している挿入と更新の数です。|  
|is_delete|**bit**|保留中の変更が削除かどうかを示します。 値**1**変更が削除であることを示します。 値が必要です**1**の@show_rowsします。|  
|rowguid|**uniqueidentifier**|変更された行を識別する GUID です。 値が必要です**1**の@show_rowsします。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 sp_showpendingchanges は、マージ レプリケーションで使用します。  
  
 sp_showpendingchanges は、マージ レプリケーションのトラブルシューティングで使用します。  
  
 sp_showpendingchanges の結果には、生成が 0 の行は含まれません。  
  
 指定されたアーティクル*記事*は指定されたパブリケーションに属していません*パブリケーション、*場合、pending_deletes および pending_ins_and_upd に対して 0 のカウントが返されます。  
  
## <a name="permissions"></a>権限  
 sp_showpendingchanges を実行できるのは、固定サーバー ロール sysadmin または固定データベース ロール db_owner のメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
