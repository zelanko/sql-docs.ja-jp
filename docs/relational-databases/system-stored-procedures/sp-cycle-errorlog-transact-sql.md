---
title: "sp_cycle_errorlog (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_cycle_errorlog_TSQL
- sp_cycle_errorlog
dev_langs: TSQL
helpviewer_keywords: sp_cycle_errorlog
ms.assetid: 61a12cbf-78a3-4052-8604-3b29d07573fd
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 8d96a243e3f5c0a095564f3bad8ba39751234c70
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spcycleerrorlog-transact-sql"></a>sp_cycle_errorlog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サーバーを再起動するときと同様に、現在のエラー ログ ファイルを閉じ、エラー ログの拡張番号を使い回します。 新しいエラー ログには、バージョンおよび著作権の情報と、新しいログが作成されたことを示す行が含まれます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_cycle_errorlog  
```  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 たびに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が開始されると、現在のエラー ログに名前が変更**'errorlog.1'**です。**'errorlog.1'**なります**errorlog.2**、 **errorlog.2**なります**errorlog.3**のようにします。 **sp_cycle_errorlog**を停止してから、サーバーを起動しないで、エラー ログ ファイルを使い回すことができます。  
  
## <a name="permissions"></a>Permissions  
 実行権限**sp_cycle_errorlog**のメンバーに制限されます、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログを使い回します。  
  
```  
EXEC sp_cycle_errorlog ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_cycle_agent_errorlog &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-cycle-agent-errorlog-transact-sql.md)  
  
  
