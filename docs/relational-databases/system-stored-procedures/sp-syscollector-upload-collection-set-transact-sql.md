---
title: sp_syscollector_upload_collection_set (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_upload_collection_set
- sp_syscollector_upload_collection_set_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_upload_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: eed9232c-2b0a-4b6a-8ba0-76b7c99f48dc
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 18e7f6ffa3e4796341a6d9e00774f0affa0931eb
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85639844"
---
# <a name="sp_syscollector_upload_collection_set-transact-sql"></a>sp_syscollector_upload_collection_set (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  コレクション セットが有効になっている場合、コレクション セット データのアップロードを開始します。  
  
> [!IMPORTANT]  
>  このストアド プロシージャは、キャッシュ モードのデータ収集およびアップロード用に構成されているコレクション セットに対してのみ使用できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syscollector_upload_collection_set [[ @collection_set_id = ] collection_set_id ]  
          , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>引数  
`[ @collection_set_id = ] collection_set_id`コレクションセットの一意なローカル識別子を設定します。 *collection_set_id*は**int**で、 *name*が NULL の場合は値が必要です。  
  
`[ @name = ] 'name'`コレクションセットの名前を指定します。 *名前*は**sysname**であり、 *collection_set_id*が NULL の場合は値を持つ必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>Remarks  
 *Collection_set_id*または*名前*のいずれかに値を指定する必要があります。両方を NULL にすることはできません。  
  
 このプロシージャは、実行中のコレクションセットのオンデマンドアップロードを開始するために使用できます。 キャッシュモードのデータ収集とアップロード用に構成されているコレクションセットに対してのみ使用できます。 このプロシージャを使用すると、ユーザーは分析に必要なデータを、予定されているアップロードを待たずに取得できます。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャを実行するには、 **dc_operator** (EXECUTE 権限を持つ) 固定データベースロールのメンバーシップが必要です。  
  
## <a name="example"></a>例  
 `Simple Collection Set` という名前のコレクション セットのオンデマンドのアップロードを実行します。  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_upload_collection_set @name = 'Simple Collection Set' ;  
```  
  
## <a name="see-also"></a>関連項目  
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [データコレクション](../../relational-databases/data-collection/data-collection.md)  
  
  
