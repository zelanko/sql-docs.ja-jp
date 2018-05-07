---
title: sp_dropextendedproc (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 10/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_dropextendedproc
- sp_dropextendedproc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropextendedproc
ms.assetid: dd93af2c-1b7d-4e39-af23-2d21d270a381
caps.latest.revision: 36
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 23361e6f28bdb87ab35a39ec68b448a60ad677d0
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="spdropextendedproc-transact-sql"></a>sp_dropextendedproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  拡張ストアド プロシージャを削除します。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 代わりに [CLR 統合](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) を使用してください。  
  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sp_dropextendedproc [ @functname = ] 'procedure'   
```  
  
## <a name="arguments"></a>引数  
 [  **@functname =**] **'***プロシージャ***'**  
 削除する拡張ストアド プロシージャの名前を指定します。 *プロシージャ*は**nvarchar (517)**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 実行する**sp_dropextendedproc**からユーザー定義の拡張ストアド プロシージャ名を削除、 [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)カタログ ビューからエントリを削除して、 [sys.extended_procedures](../../relational-databases/system-catalog-views/sys-extended-procedures-transact-sql.md)カタログ ビューです。 このストアド プロシージャをでのみ実行することができます、**マスター**データベース。  
  
**sp_dropextendedproc**もシステム拡張ストアド プロシージャは削除されません。 システム管理者が、拡張ストアド プロシージャに対する EXECUTE 権限を拒否する代わりに、**パブリック**ロール。  
  
 **sp_dropextendedproc**トランザクション内で実行することはできません。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_dropextendedproc**です。  
  
## <a name="examples"></a>使用例  
 次の例では削除、`xp_hello`拡張ストアド プロシージャです。  
  
> [!NOTE]  
>  この拡張ストアド プロシージャは既に存在している必要があります。存在しない場合はエラー メッセージが返されます。  
  
```  
USE master;  
GO  
EXEC sp_dropextendedproc 'xp_hello';  
```  
  
## <a name="see-also"></a>参照  
 [sp_addextendedproc &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_helpextendedproc &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
