---
title: sp_syscollector_run_collection_set (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_run_collection_set_TSQL
- sp_syscollector_run_collection_set
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_run_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: 7bbaee48-dfc7-45c0-b11f-c636b6a7e720
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 88b1cd8aaf95da010883faa7033c0bd6bf3cd2a5
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82809808"
---
# <a name="sp_syscollector_run_collection_set-transact-sql"></a>sp_syscollector_run_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  コレクターが既に有効になっており、コレクション セットが非キャッシュ コレクション モード用に構成されている場合、コレクション セットを開始します。  
  
> [!NOTE]  
>  キャッシュコレクションモード用に構成されているコレクションセットに対して実行する場合、この手順は失敗します。  
  
 sp_syscollector_run_collection_set を使用すると、ユーザーはオンデマンドのデータ スナップショットを取得できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syscollector_run_collection_set [[ @collection_set_id = ] collection_set_id ]  
          , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>引数  
`[ @collection_set_id = ] collection_set_id`コレクションセットの一意なローカル識別子を設定します。 *collection_set_id*は**int**で、 *name*が NULL の場合は値が必要です。  
  
`[ @name = ] 'name'`コレクションセットの名前を指定します。 *名前*は**sysname**であり、 *collection_set_id*が NULL の場合は値を持つ必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>Remarks  
 *Collection_set_id*または*名前*には値を指定する必要があります。どちらも NULL にすることはできません。  
  
 この手順では、コレクションを開始し、指定されたコレクションセットのジョブをアップロードします。また、コレクションセットの** \@ collection_mode**が非キャッシュ (1) に設定されている場合は、直ちにコレクションエージェントジョブを開始します。 詳細については、「 [sp_syscollector_create_collection_set &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md)」を参照してください。  
  
 sp_sycollector_run_collection_set は、スケジュールを持たないコレクション セットの実行にも使用できます。  
  
## <a name="permissions"></a>アクセス許可  
 このプロシージャを実行するには、 **dc_operator** (EXECUTE 権限を持つ) 固定データベースロールのメンバーシップが必要です。  
  
## <a name="example"></a>例  
 対応する ID を使ってコレクション セットを開始します。  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_run_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>参照  
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [データコレクション](../../relational-databases/data-collection/data-collection.md)  
  
  
