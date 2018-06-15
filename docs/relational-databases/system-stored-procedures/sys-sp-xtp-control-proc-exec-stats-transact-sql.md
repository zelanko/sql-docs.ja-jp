---
title: sys.sp_xtp_control_proc_exec_stats (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sp_xtp_control_proc_exec_stats
- sys.sp_xtp_control_proc_exec_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_xtp_control_proc_exec_stats
ms.assetid: f5119808-76a1-4522-8529-9e02ee39adcb
caps.latest.revision: 15
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4423664cd7cf7edcfa628a51c85653bf3745fef6
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254950"
---
# <a name="sysspxtpcontrolprocexecstats-transact-sql"></a>sys.sp_xtp_control_proc_exec_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  インスタンスに関するネイティブ コンパイル ストアド プロシージャの統計コレクションを有効にします。  
  
 ネイティブ コンパイル ストアド プロシージャのクエリ レベルで統計コレクションを有効にするを参照してください。 [sys.sp_xtp_control_query_exec_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
sp_xtp_control_proc_exec_stats [ [ @new_collection_value = ] collection_value ], [ @old_collection_value]  
```  
  
## <a name="arguments"></a>引数  
 @new_collection_value = *value*  
 プロシージャ レベルの統計コレクションが有効 (1) であるか、無効 (0) であるかを示します。  
  
 @new_collection_value 0 に設定されている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]したり、データベースを起動します。  
  
 @old_collection_value = *value*  
 現在の状態を返します。  
  
## <a name="return-code"></a>リターン コード  
 成功した場合は 0。 失敗した場合は 0 以外の値。  
  
## <a name="permissions"></a>権限  
 固定 sysadmin ロールのメンバーシップが必要です。  
  
## <a name="code-samples"></a>コード サンプル  
 設定する@new_collection_valueとクエリの値を @new_collection_value:  
  
```  
exec [sys].[sp_xtp_control_proc_exec_stats] @new_collection_value = 1  
declare @c bit  
exec sp_xtp_control_proc_exec_stats @old_collection_value=@c output  
select @c as 'collection status'  
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
