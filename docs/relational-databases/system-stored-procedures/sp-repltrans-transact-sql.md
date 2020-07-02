---
title: sp_repltrans (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_repltrans_TSQL
- sp_repltrans
helpviewer_keywords:
- sp_repltrans
ms.assetid: 738e2322-335b-44fa-820e-f31c02743978
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ea8d8c948c3a04a5c63377f5209fbe946d945c09
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85640004"
---
# <a name="sp_repltrans-transact-sql"></a>sp_repltrans (Transact-sql)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  パブリケーション データベース トランザクション ログ内にあって、レプリケーションのマークは付いているがディストリビュートされたマークがまだ付いていないすべてのトランザクションの結果セットを返します。 このストアドプロシージャは、パブリッシャー側でパブリケーションデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_repltrans  
```  
  
## <a name="result-sets"></a>結果セット  
 **sp_repltrans**は、実行元のパブリケーションデータベースに関する情報を返します。これにより、現在ディストリビュートされていないトランザクション (つまり、ディストリビューターにまだ送信されていないトランザクションログに残っているトランザクション) を表示できます。 結果セットは、各トランザクションの最初と最後のレコードのログ シーケンス番号を表示します。 **sp_repltrans**は[sp_replcmds &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)に似ていますが、トランザクションのコマンドは返されません。  
  
## <a name="remarks"></a>Remarks  
 **sp_repltrans**は、トランザクションレプリケーションで使用します。  
  
 **sp_repltrans**は、以外のパブリッシャーではサポートされていません [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_repltrans**を実行できるのは、固定サーバーロール**sysadmin**または固定データベースロール**db_owner**のメンバーだけです。  
  
## <a name="see-also"></a>関連項目  
 [sp_repldone &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
