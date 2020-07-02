---
title: sp_mergedummyupdate (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_mergedummyupdate_TSQL
- sp_mergedummyupdate
helpviewer_keywords:
- sp_mergedummyupdate
ms.assetid: b834f7f6-9588-4d59-a3e2-83d8e8e722e1
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ecb59448ff76114d25dbb8422cf7dc1fefc44e15
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85640272"
---
# <a name="sp_mergedummyupdate-transact-sql"></a>sp_mergedummyupdate (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  指定した行でダミーを更新し、その更新が次のマージで再送されるようにします。 このストアドプロシージャは、パブリッシャー、パブリケーションデータベース、またはサブスクライバー側でサブスクリプションデータベースに対して実行できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_mergedummyupdate [ @source_object =] 'source_object', [ @rowguid =] 'rowguid'  
```  
  
## <a name="arguments"></a>引数  
`[ @source_object = ] 'source_object'`ソースオブジェクトの名前を指定します。 *source_object*は**nvarchar (386)**,、既定値はありません。  
  
`[ @rowguid = ] 'rowguid'`行識別子を示します。 *rowguid*は**uniqueidentifier**,、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>Remarks  
 **sp_mergedummyupdate**は、マージレプリケーションで使用します。  
  
 **sp_mergedummyupdate**は、レプリケーション競合表示モジュール (Wzcnflct.exe) に独自の代替手段を記述する場合に便利です。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_mergedummyupdate**を実行できるのは、 **db_owner**固定データベースロールのメンバーだけです。  
  
## <a name="see-also"></a>関連項目  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
