---
title: snapshots.fn_trace_getdata (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- snapshots.fn_trace_getdata
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots.fn_trace_getdata function
ms.assetid: ac28ef48-f4f4-4bf2-ba22-d44e1be88172
caps.latest.revision: 19
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 63e524e8a3e14abdb2ca96d4378391e3d25746a0
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="snapshotsfntracegetdata-transact-sql"></a>snapshots.fn_trace_getdata (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  この関数は、指定したトレースでキャプチャされたすべてのイベントを返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
snapshots.fn_trace_gettable ( trace_info_id, start_time, end_time )  
```  
  
## <a name="arguments"></a>引数  
 *trace_info_id*  
 ウェアハウス データベースの管理データに snapshots.trace_info テーブルの主キーの一意の識別子。 *trace_info_id*は**int**です。  
  
 *start_time*  
 トレースが開始された時刻です。 *start_time*は**datetime**です。  
  
 *end_time*  
 トレースが終了した時刻です。 *end_time*は**datetime**です。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|\<すべてのトレース列 >|\<異なります >|管理データ ウェアハウス データベースの snapshots.trace_data テーブルからのトレース データ。<br /><br /> 次のクエリを使用すると、指定したトレースに対応する一連の列を取得できます。<br /><br /> `SELECT * FROM sys.trace_columns`<br /><br /> **注:** snapshots.fn_trace_gettable 関数から返される列は、sys.trace_columns システム ビューで name 列の値に対応します。 この関数から GroupID 列が返されない点のみが異なります。|  
  
## <a name="permissions"></a>権限  
 mdw_reader に対する SELECT 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [データ コレクション](../../relational-databases/data-collection/data-collection.md)  
  
  
