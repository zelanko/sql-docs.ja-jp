---
title: sp_showpendingchanges (Transact-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_showpendingchanges
- sp_showpendingchanges_TSQL
helpviewer_keywords:
- sp_showpendingchanges
ms.assetid: 8013a792-639d-4550-b262-e65d30f9d291
author: stevestein
ms.author: sstein
ms.openlocfilehash: cc02137e23c3871066c01ae1a7e9655232c349c7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68032900"
---
# <a name="spshowpendingchanges-transact-sql"></a>sp_showpendingchanges (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  レプリケートするを待機している変更を示す結果セットを返します。 このストアド プロシージャは、パブリッシャー側のパブリケーション データベースとサブスクライバーのサブスクリプション データベースで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
> [!NOTE]  
>  この手順では、変更し、それらの変更に関連する行の数の概算値を提供します。 たとえば、プロシージャは、パブリッシャーまたはサブスクライバーの両方と同時にではなくいずれかから情報を取得します。 プロシージャで推定よりも、同期する変更の小さいセットについては、他のノードに格納されている可能性があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_showpendingchanges [ [ @destination_server = ] 'destination_server' ]  
    [ , [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article']  
    [ , [ @show_rows = ] show_rows]  
```  
  
## <a name="arguments"></a>引数  
 [ @destination_server **=** ] **'***destination_server***'**  
 レプリケートされた変更が適用されるサーバーの名前です。 *destination_server*は**sysname**既定値は NULL です。  
  
 [ @publication **=** ] **'***パブリケーション***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**既定値は NULL です。 ときに*パブリケーション*指定すると、結果は、指定されたパブリケーションのみに制限されています。  
  
 [ @article **=** ] **'***記事***'**  
 アーティクルの名前です。 *記事*は**sysname**既定値は NULL です。 ときに*記事*指定すると、結果は、指定したアーティクルのみに制限されています。  
  
 [ @show_rows **=** ] *show_rows*  
 結果セットが、保留中の既定の値の変更に関するより具体的な情報を格納するかどうかを指定します。 **0**します。 値の場合**1**を指定すると、結果セットには、列の is_delete 列と rowguid が含まれています。  
  
## <a name="result-set"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|destination_server|**sysname**|変更がレプリケートされているサーバーの名前。|  
|pub_name|**sysname**|パブリケーションの名前を指定します。|  
|destination_db_name|**sysname**|変更がレプリケートされているデータベースの名前。|  
|is_dest_subscriber|**bit**|ことを示します、変更がサブスクライバーにレプリケートされています。 値**1**変更がサブスクライバーにレプリケートされていることを示します。 **0**変更がパブリッシャーにレプリケートされていることを意味します。|  
|article_name|**sysname**|変更が行われたテーブルのアーティクルの名前です。|  
|pending_deletes|**int**|レプリケートするを待機している削除の数。|  
|pending_ins_and_upd|**int**|挿入とレプリケートを待機している更新プログラムの数。|  
|is_delete|**bit**|保留中の変更が削除かどうかを示します。 値**1**変更が削除であることを示します。 値が必要です**1**の@show_rowsします。|  
|rowguid|**uniqueidentifier**|変更された行を識別する GUID です。 値が必要です**1**の@show_rowsします。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 sp_showpendingchanges は、マージ レプリケーションで使用します。  
  
 sp_showpendingchanges は、マージ レプリケーションのトラブルシューティングを行うときに使用されます。  
  
 sp_showpendingchanges の結果には、生成が 0 の行は含まれません。  
  
 指定されたアーティクル*記事*は指定されたパブリケーションに属していません*パブリケーション*場合、pending_deletes および pending_ins_and_upd の 0 のカウントが返されます。  
  
## <a name="permissions"></a>アクセス許可  
 sp_showpendingchanges を実行できるのは、固定サーバー ロール sysadmin または固定データベース ロール db_owner のメンバーだけです。  
  
## <a name="see-also"></a>関連項目  
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
