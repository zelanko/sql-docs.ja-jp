---
title: sp_delete_targetserver (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_delete_targetserver
- sp_delete_targetserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_targetserver
ms.assetid: cc438701-ad91-419d-9f23-ebc4c548c700
caps.latest.revision: 22
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a4674f0bd6d8bbcb3ed456f74a0ee034c6f25db9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="spdeletetargetserver-transact-sql"></a>sp_delete_targetserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたサーバーを利用可能な対象サーバーの一覧から削除します。  
   
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_delete_targetserver [ @server_name = ] 'server'   
     [ , [ @clear_downloadlist = ] clear_downloadlist ]  
     [ , [ @post_defection = ] post_defection ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@server_name=** ] **'***server***'**  
 利用可能なサーバーの対象から削除するサーバーの名前を指定します。 *サーバー*は**nvarchar (30)**、既定値はありません。  
  
 [ **@clear_downloadlist=** ] *clear_downloadlist*  
 対象サーバーのダウンロード一覧を消去するかどうかを指定します。 *clear_downloadlist*は型です。**ビット**、既定値は**1**です。 ときに*clear_downloadlist*は**1**プロシージャが、サーバーを削除する前に、サーバーのダウンロード一覧をクリアします。 ときに*clear_downloadlist*は**0**、ダウンロード一覧は消去されません。  
  
 [ **@post_defection=** ] *post_defection*  
 対象サーバーに参加解除の命令を通知するかどうかを指定します。 *post_defection*は型です。**ビット**、既定値は 1 です。 ときに*post_defection*は**1**サーバーを削除する前に、対象サーバーを参加解除の命令が通知されます。 ときに*post_defection*は**0**プロシージャが、対象サーバーを参加解除の命令が通知されません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 対象サーバーを削除するのには、通常の方法が呼び出されて**sp_msx_defect**対象サーバーでします。 使用して**sp_delete_targetserver**手動で参加解除が必要な場合にのみです。  
  
## <a name="permissions"></a>権限  
 このストアド プロシージャを実行するユーザーに付与する必要があります、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、サーバーを削除する`LONDON1`可能なジョブ サーバーからです。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_targetserver  
  @server_name = N'LONDON1' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_help_targetserver &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-targetserver-transact-sql.md)   
 [sp_msx_defect &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-msx-defect-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
