---
title: sp_getmergedeletetype (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_getmergedeletetype
- sp_getmergedeletetype_TSQL
helpviewer_keywords:
- sp_getmergedeletetype
ms.assetid: 64450e4d-844d-4176-874e-f3845536f7d2
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 04437ebf7d33c81a847fe8f17ca74a0cb68b4279
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32994081"
---
# <a name="spgetmergedeletetype-transact-sql"></a>sp_getmergedeletetype (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ削除の型を返します。 このストアド プロシージャは、パブリッシャー側のパブリケーション データベースまたはサブスクライバーのサブスクリプション データベースで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_getmergedeletetype [ @source_object = ] 'source_object', [ @rowguid =] 'rowguid', [ @delete_type=] delete_type OUTPUT  
```  
  
## <a name="arguments"></a>引数  
 [  **@source_object =**] **'***source_object***'**  
 ソース オブジェクトの名前を指定します。 *source_object*は**nvarchar (386)**、既定値はありません。  
  
 [  **@rowguid=**] **'***rowguid***'**  
 削除の型の行識別子を指定します。 *rowguid*は**uniqueidentifier**、既定値はありません。  
  
 [  **@delete_type=**] *delete_type* **出力**  
 削除の種類を示すコードを指定します。 *delete_type*は**int**、既定値はありません。 *delete_type*も出力パラメーターでは、これらの値のいずれかになります。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|ユーザー削除|  
|**5**|部分削除|  
|**6**|システム削除|  
  
## <a name="remarks"></a>解説  
 **sp_getmergedeletetype**はマージ レプリケーションで使用します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_getmergedeletetype**です。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
