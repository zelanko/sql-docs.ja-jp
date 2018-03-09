---
title: "sp_repltrans (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_repltrans_TSQL
- sp_repltrans
helpviewer_keywords:
- sp_repltrans
ms.assetid: 738e2322-335b-44fa-820e-f31c02743978
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2123841f5819842df4a4833e1a243dbfbeddf7dc
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sprepltrans-transact-sql"></a>sp_repltrans (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリケーション データベース トランザクション ログ内にあって、レプリケーションのマークは付いているがディストリビュートされたマークがまだ付いていないすべてのトランザクションの結果セットを返します。 このストアド プロシージャは、パブリッシャー側のパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_repltrans  
```  
  
## <a name="result-sets"></a>結果セット  
 **sp_repltrans**実行元となることが、まだディストリビュートされていないトランザクションを表示することができます、パブリケーション データベースに関する情報を返します (に送信されていないトランザクション ログに残っているトランザクション、ディストリビューターで)。 結果セットは、各トランザクションの最初と最後のレコードのログ シーケンス番号を表示します。 **sp_repltrans**に似ていますが[sp_replcmds (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md)トランザクションのコマンドは返しません。  
  
## <a name="remarks"></a>解説  
 **sp_repltrans**トランザクション レプリケーションで使用します。  
  
 **sp_repltrans**はサポートされません以外[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_repltrans**です。  
  
## <a name="see-also"></a>参照  
 [sp_repldone と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
