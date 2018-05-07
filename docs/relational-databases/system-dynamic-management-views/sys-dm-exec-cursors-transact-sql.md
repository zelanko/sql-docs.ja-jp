---
title: sys.dm_exec_cursors (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_cursors_TSQL
- dm_exec_cursors
- dm_exec_cursors_TSQL
- sys.dm_exec_cursors
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_cursors dynamic management function
ms.assetid: f520b63c-36af-40f1-bf71-6901d6331d3d
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2793f7eed7103668141a0197216dfd2ab8efd061
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmexeccursors-transact-sql"></a>sys.dm_exec_cursors (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  各種データベースで開いているカーソルに関する情報を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dm_exec_cursors (session_id | 0 )  
```  
  
## <a name="arguments"></a>引数  
 *session_id* | 0  
 セッションの ID を指定します。 場合*session_id*を指定すると、この関数は、指定したセッションのカーソルに関する情報を返します。  
  
 0 を指定した場合、この関数ではすべてのセッションのすべてのカーソルに関する情報が返されます。  
  
## <a name="table-returned"></a>返されるテーブル  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|カーソルを保持しているセッションの ID。|  
|**cursor_id**|**int**|カーソル オブジェクトの ID。|  
|**name**|**nvarchar (256)**|ユーザーによって定義されたカーソルの名前。|  
|**プロパティ**|**nvarchar (256)**|カーソルのプロパティ。 次のプロパティの値を連結して、この列の値を作成します。<br />宣言インターフェイス<br />カーソルの種類 <br />カーソルの同時実行<br />カーソルのスコープ<br />カーソルの入れ子のレベル<br /><br /> たとえば、この列に返される値があります"TSQL&#124;動的&#124;Optimistic &#124; Global (0)"です。|  
|**sql_handle**|**varbinary(64)**|カーソルを宣言したバッチのテキストへのハンドル。|  
|**statement_start_offset**|**int**|現在実行中のバッチまたはストアド プロシージャに含まれる、現在実行中のステートメントが開始されるまでの文字数。 組み合わせて使用することができます、 **sql_handle**、 **statement_end_offset**、および[sys.dm_exec_sql_text](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)動的管理関数を取得する、現在要求に対してステートメントを実行します。|  
|**statement_end_offset**|**int**|現在実行中のバッチまたはストアド プロシージャに含まれる、現在実行中のステートメントが終了するまでの文字数。 組み合わせて使用することができます、 **sql_handle**、 **statement_start_offset**、および**sys.dm_exec_sql_text**動的管理関数を取得する、現在要求に対してステートメントを実行します。|  
|**plan_generation_num**|**bigint**|再コンパイル後、プランのインスタンス間で区別するために使用できるシーケンス番号。|  
|**creation_time**|**datetime**|カーソルが作成されたタイムスタンプ。|  
|**is_open**|**bit**|カーソルが開いているかどうかを示します。|  
|**is_async_population**|**bit**|バックグラウンド スレッドで KEYSET または STATIC カーソルが非同期に作成されているかどうかを示します。|  
|**is_close_on_commit**|**bit**|CURSOR_CLOSE_ON_COMMIT を使用して、カーソルが宣言されているかどうかを示します。<br /><br /> 1 = カーソルはトランザクションが終了したときに閉じられます。|  
|**fetch_status**|**int**|前回のカーソルのフェッチの状態。 これは、返される最後@FETCH_STATUS値。|  
|**fetch_buffer_size**|**int**|フェッチ バッファーのサイズに関する情報。<br /><br /> 1 = Transact-SQL カーソル。 API カーソルの場合は、より高い値に設定される可能性があります。|  
|**fetch_buffer_start**|**int**|FAST_FORWARD と DYNAMIC カーソルの場合で、カーソルが開いていないか、カーソルが最初の行より前にあるときは 0 が返され、 それ以外のときは -1 が返されます。<br /><br /> STATIC と KEYSET カーソルの場合で、カーソルが開いていないときは 0 が返され、カーソルが最後の行より後にあるときは -1 が返されます。<br /><br /> それ以外のときは、カーソルがある場所の行番号が返されます。|  
|**ansi_position**|**int**|フェッチ バッファー内のカーソル位置。|  
|**worker_time**|**bigint**|カーソルを実行するワーカーによって消費された時間 (ミリ秒単位)。|  
|**reads**|**bigint**|カーソルで実行された読み取りの数。|  
|**書き込み**|**bigint**|カーソルで実行された書き込みの数。|  
|**dormant_duration**|**bigint**|カーソルの前回のクエリ (開くまたはフェッチ) が開始されてから経過した時間 (ミリ秒単位)。|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="remarks"></a>解説  
 次の表は、カーソル宣言インターフェイスの説明と、プロパティ列に返される値です。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|API (API)|カーソルは、データ アクセス API (ODBC、OLEDB) の 1 つを使用して宣言されています。|  
|TSQL|カーソルは、Transact-SQL DECLARE CURSOR 構文を使用して宣言されています。|  
  
 次の表は、カーソルの種類に関する説明と、プロパティ列に返される値です。  
  
|型|Description|  
|----------|-----------------|  
|Keyset|カーソルはキーセットとして宣言されています。|  
|Dynamic|カーソルは動的として宣言されています。|  
|スナップショット|カーソルはスナップショットまたは静的として宣言されています。|  
|Fast_Forward|カーソルは高速順方向として宣言されています。|  
  
 次の表は、カーソルの同時実行に関する説明と、プロパティ列に返される値です。  
  
|同時実行|Description|  
|-----------------|-----------------|  
|[読み取り専用]|カーソルは読み取り専用として宣言されています。|  
|Scroll Lock|カーソルでスクロール ロックが使用されています。|  
|オプティミスティック|カーソルでオプティミスティック同時実行制御が使用されています。|  
  
 次の表は、カーソルのスコープに関する説明と、プロパティ列に返される値です。  
  
|スコープ|Description|  
|-----------|-----------------|  
|Local|カーソルのスコープは、カーソルが作成されたバッチ、ストアド プロシージャ、またはトリガーに対してローカルです。|  
|Global|カーソルのスコープは、接続に対してグローバルです。|  
  
## <a name="examples"></a>使用例  
  
### <a name="a-detecting-old-cursors"></a>A. 古いカーソルを検出する  
 この例では、サーバー上で、指定した 36 時間よりも長く開いているカーソルに関する情報を返します。  
  
```  
SELECT creation_time, cursor_id, name, c.session_id, login_name   
FROM sys.dm_exec_cursors(0) AS c   
JOIN sys.dm_exec_sessions AS s ON c.session_id = s.session_id   
WHERE DATEDIFF(hh, c.creation_time, GETDATE()) > 36;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [動的管理ビューと動的管理関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [実行関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
  
  

