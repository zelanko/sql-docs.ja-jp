---
title: sp_xtp_flush_temporal_history |Microsoft Docs
ms.custom: ''
ms.date: 02/21/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sp_xtp_flush_temporal_history
- sp_xtp_flush_temporal_history_TSQL
- sys.sp_xtp_flush_temporal_history
- sys.sp_xtp_flush_temporal_history_TSQL
helpviewer_keywords:
- sp_xtp_flush_temporal_history
ms.assetid: 322e3170-93f8-468a-a123-104ce7bd7fad
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 25f6c9bd1aa9cbebd9b445399442d47eff1abe72
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47758690"
---
# <a name="spxtpflushtemporalhistory-transact-sql"></a>sp_xtp_flush_temporal_history (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  ディスク ベースの履歴テーブルにステージング テーブルをメモリ内からコミットされたすべての行を移動するデータのフラッシュのタスクを呼び出します。  

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sys.sp_xtp_flush_temporal_history @schema_name, @object_name  
  
```  
  
## <a name="arguments"></a>引数  
 *@schema_name*  
 現在または一時的なテーブルのスキーマ名  
  
 *@object_name*  
 現在または一時的なテーブルの名前  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または >0 (失敗)  
  
## <a name="permissions"></a>アクセス許可  
 Db_owner アクセス許可が必要です。  
  
## <a name="see-also"></a>参照  
 [メモリ最適化およびシステム バージョン管理されたテンポラル テーブルのパフォーマンスに関する考慮事項](../../relational-databases/tables/memory-optimized-system-versioned-temporal-tables-performance.md)  
  
  
