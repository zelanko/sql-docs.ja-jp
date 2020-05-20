---
title: sp_getmergedeletetype (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_getmergedeletetype
- sp_getmergedeletetype_TSQL
helpviewer_keywords:
- sp_getmergedeletetype
ms.assetid: 64450e4d-844d-4176-874e-f3845536f7d2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 971226c9f53932bf8214304a7c166ad75a11853c
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82833218"
---
# <a name="sp_getmergedeletetype-transact-sql"></a>sp_getmergedeletetype (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ削除の型を返します。 このストアドプロシージャは、パブリッシャー側でパブリケーションデータベースに対して実行されるか、サブスクライバー側でサブスクリプションデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_getmergedeletetype [ @source_object = ] 'source_object', [ @rowguid =] 'rowguid', [ @delete_type=] delete_type OUTPUT  
```  
  
## <a name="arguments"></a>引数  
`[ @source_object = ] 'source_object'`ソースオブジェクトの名前を指定します。 *source_object*は**nvarchar (386)**,、既定値はありません。  
  
`[ @rowguid = ] 'rowguid'`削除の種類の行識別子を入力します。 *rowguid*は**uniqueidentifier**,、既定値はありません。  
  
`[ @delete_type = ] delete_type OUTPUT`削除の種類を示すコードを指定します。 *delete_type*は**int**,、既定値はありません。 *delete_type*は出力パラメーターでもあり、次のいずれかの値を指定できます。  
  
|[値]|説明|  
|-----------|-----------------|  
|**1**|ユーザーの削除|  
|**5**|部分削除|  
|**6**|システムの削除|  
  
## <a name="remarks"></a>解説  
 **sp_getmergedeletetype**は、マージレプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_getmergedeletetype**を実行できるのは、固定サーバーロール**sysadmin**または固定データベースロール**db_owner**のメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
