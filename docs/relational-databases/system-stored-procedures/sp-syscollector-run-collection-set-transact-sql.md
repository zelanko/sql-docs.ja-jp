---
title: "sp_syscollector_run_collection_set (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_syscollector_run_collection_set_TSQL
- sp_syscollector_run_collection_set
dev_langs: TSQL
helpviewer_keywords:
- sp_syscollector_run_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: 7bbaee48-dfc7-45c0-b11f-c636b6a7e720
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ca014293d64b0782d4844794efb5528849d0ecf9
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="spsyscollectorruncollectionset-transact-sql"></a>sp_syscollector_run_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  コレクターが既に有効になっており、コレクション セットが非キャッシュ コレクション モード用に構成されている場合、コレクション セットを開始します。  
  
> [!NOTE]  
>  このプロシージャをキャッシュ コレクション モード用に構成されているコレクション セットに対して実行すると、失敗します。  
  
 sp_syscollector_run_collection_set を使用すると、ユーザーはオンデマンドのデータ スナップショットを取得できます。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_syscollector_run_collection_set [[ @collection_set_id = ] collection_set_id ]  
          , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>引数  
 [  **@collection_set_id =** ] *collection_set_id*  
 コレクション セットの一意なローカル識別子を指定します。 *collection_set_id*は**int**場合、値が必要と*名前*は NULL です。  
  
 [  **@name =** ] **'***名前***'**  
 コレクション セットの名前を指定します。 *名前*は**sysname**場合、値が必要と*collection_set_id*は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 いずれか*collection_set_id*または*名前*必要があります値を持つ、どちらも NULL をすることはできません。  
  
 この手順は、コレクションを開始し、アップロード ジョブを指定されたコレクション セットおよびコレクション セットがある場合に、コレクション エージェント ジョブをすぐに開始されます、  **@collection_mode** 非キャッシュ (1) に設定します。 詳細については、「 [sp_syscollector_create_collection_set (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md).  
  
 sp_sycollector_run_collection_set は、スケジュールを持たないコレクション セットの実行にも使用できます。  
  
## <a name="permissions"></a>Permissions  
 メンバーシップが必要、 **dc_operator** (EXECUTE 権限) を持つ固定データベース ロールにこのプロシージャを実行します。  
  
## <a name="example"></a>例  
 対応する ID を使ってコレクション セットを開始します。  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_run_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [[データ コレクション]](../../relational-databases/data-collection/data-collection.md)  
  
  
