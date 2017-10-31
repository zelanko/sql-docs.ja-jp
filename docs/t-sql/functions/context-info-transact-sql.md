---
title: "CONTEXT_INFO (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONTEXT_INFO_TSQL
- CONTEXT_INFO
dev_langs:
- TSQL
helpviewer_keywords:
- CONTEXT_INFO function
- Multiple Active Result Sets
- context information [SQL Server]
- MARS [SQL Server]
- session context information [SQL Server]
ms.assetid: 571320f5-7228-4b0e-9d01-ab732d2d1eab
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dd261b2f7f1cc4234792bec66c3662d6d9b8dcd8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="contextinfo--transact-sql"></a>CONTEXT_INFO (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

返します、 **context_info**を使用して、現在のセッションまたはバッチに対して設定された値、 [SET CONTEXT_INFO](../../t-sql/statements/set-context-info-transact-sql.md)ステートメントです。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
CONTEXT_INFO()  
```  
  
## <a name="return-value"></a>戻り値
値**context_info**です。
  
場合**context_info**が設定されませんでした。
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は NULL を返します。  
-   [!INCLUDE[ssSDS](../../includes/sssds-md.md)]セッション固有の一意の GUID を返します。  
  
## <a name="remarks"></a>解説  
複数のアクティブな結果セット (MARS) によって、アプリケーションは複数のバッチまたは要求を同じ接続上で同時に実行できます。 MARS 接続上の 1 つのバッチで SET CONTEXT_INFO を実行する場合、CONTEXT_INFO 関数を SET ステートメントと同時に実行すると、新しいコンテキスト値が返されます。 接続上のその他の 1 つ以上のバッチで CONTEXT_INFO 関数を実行するには、SET ステートメントの実行が完了した後のバッチで開始しないと、新しい値は返されません。
  
## <a name="permissions"></a>Permissions  
特に必要な権限はありません。 コンテキスト情報にも格納、 **sys.dm_exec_requests**、 **sys.dm_exec_sessions**、および**sys.sysprocesses**システム ビューがビューを直接クエリSELECT および VIEW SERVER STATE 権限が必要です。
  
## <a name="examples"></a>使用例  
次の簡単な例のセット、 **context_info**値`0x1256698456`、しを使用して、`CONTEXT_INFO`値を取得する関数。
  
```sql
SET CONTEXT_INFO 0x1256698456;  
GO  
SELECT CONTEXT_INFO();  
GO  
```  
  
## <a name="see-also"></a>参照
[SET CONTEXT_INFO & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-context-info-transact-sql.md)
  
  

