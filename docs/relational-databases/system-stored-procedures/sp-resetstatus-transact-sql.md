---
title: sp_resetstatus (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_resetstatus
- sp_resetstatus_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_resetstatus
ms.assetid: b892727f-ea3b-4b94-88d9-f2386ad4962c
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 556653574734c81776b5504500bcf2fadb004228
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="spresetstatus-transact-sql"></a>sp_resetstatus (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  未確認のデータベースの状態をリセットします。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用して[ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_resetstatus [ @dbname = ] 'database'  
```  
  
## <a name="arguments"></a>引数  
 [ @dbname=] '*データベース*'  
 リセットするデータベースの名前を指定します。 *データベース*は**sysname**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 sp_resetstatus では、データベースの未確認フラグがオフにされます。 また、このプロシージャによって、sys.databases 内の指定のデータベースのモード列と状態列が更新されます。 このプロシージャを実行する前には、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログを検討し、すべての問題を解決しておいてください。 sp_resetstatus を実行した後は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを停止し再起動します。  
  
 データベースは、さまざまな理由で未確認の状態になります。 その原因としては、オペレーティング システムによるデータベース リソースへのアクセス拒否や、データベース ファイルが利用できな場合や損傷している場合が考えられます。  
  
## <a name="permissions"></a>権限  
 sysadmin 固定サーバー ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例のリセットの状態、`AdventureWorks2012`データベース。  
  
```  
EXEC sp_resetstatus 'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
