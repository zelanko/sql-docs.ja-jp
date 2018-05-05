---
title: sp_mergedummyupdate (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
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
- sp_mergedummyupdate_TSQL
- sp_mergedummyupdate
helpviewer_keywords:
- sp_mergedummyupdate
ms.assetid: b834f7f6-9588-4d59-a3e2-83d8e8e722e1
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 3d31ad74486c8be2b964f4dd3f02c5b5a04ac0b7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spmergedummyupdate-transact-sql"></a>sp_mergedummyupdate (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定した行でダミーを更新し、その更新が次のマージで再送されるようにします。 パブリッシャーのパブリケーション データベースまたはサブスクライバーのサブスクリプション データベースに対して、このストアド プロシージャを実行できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_mergedummyupdate [ @source_object =] 'source_object', [ @rowguid =] 'rowguid'  
```  
  
## <a name="arguments"></a>引数  
 [  **@source_object=**] **'***source_object***'**  
 ソース オブジェクトの名前を指定します。 *source_object*は**nvarchar (386)**、既定値はありません。  
  
 [  **@rowguid=**] **'***rowguid***'**  
 行の識別子を指定します。 *rowguid*は**uniqueidentifier**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_mergedummyupdate**はマージ レプリケーションで使用します。  
  
 **sp_mergedummyupdate**レプリケーション競合表示モジュール (Wzcnflct.exe) する代わりに、独自に記述する場合に便利です。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **db_owner**固定データベース ロールが実行できる**sp_mergedummyupdate**です。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
