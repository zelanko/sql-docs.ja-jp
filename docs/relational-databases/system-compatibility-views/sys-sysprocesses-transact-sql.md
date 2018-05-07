---
title: sys.sysprocesses (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sysprocesses_TSQL
- sys.sysprocesses_TSQL
- sys.sysprocesses
- sysprocesses
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysprocesses compatibility view
- sysprocesses system table
ms.assetid: 60a36d36-54b3-4bd6-9cac-702205a21b16
caps.latest.revision: 57
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: c3a27e699312793e734d9a94680677eb509a2bd5
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="syssysprocesses-transact-sql"></a>sys.sysprocesses (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  インスタンスで実行されているプロセスに関する情報を含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 これらのプロセスは、クライアント プロセスでもシステム プロセスでもかまいません。 sysprocesses にアクセスするには、master データベースのコンテキストからアクセスするか、3 つの要素から成る名前 (master.dbo.sysprocesses) を使用する必要があります。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|spid|**smallint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セッション id です。|  
|kpid|**smallint**|Windows のスレッド ID です。|  
|blocked|**smallint**|要求をブロックしているセッションの ID。 この列が NULL の場合は、要求がブロックされていないか、ブロックしているセッションのセッション情報が使用または識別できません。<br /><br /> -2 = ブロックしているリソースは、孤立した分散トランザクションが所有しています。<br /><br /> -3 = ブロックしているリソースは、遅延復旧トランザクションが所有しています。<br /><br /> -4 = 内部ラッチの状態遷移のため、ブロックしているラッチの所有者のセッション ID を特定できませんでした。|  
|waittype|**binary(2)**|予約されています。|  
|waittime|**bigint**|現在の待機時間 (ミリ秒単位) です。<br /><br /> 0 = プロセスは待機していません。|  
|lastwaittype|**nchar(32)**|最後または現在の待機の種類の名前を示す文字列です。|  
|waitresource|**nchar(256)**|ロックされているリソースのテキスト表示です。|  
|dbid|**smallint**|プロセスが現在使用しているデータベースの ID です。|  
|uid|**smallint**|コマンドを実行したユーザーの ID です。 ユーザーとロールの数が 32,767 を超える場合は、オーバーフローが発生するか NULL が返されます。|  
|cpu|**int**|プロセスの累積 CPU 時間です。 このエントリは、SET STATISTICS TIME オプションがオンかオフかにかかわらず、すべてのプロセスについて更新されます。|  
|physical_io|**bigint**|そのプロセスの累積ディスク読み書き数です。|  
|memusage|**int**|このプロセスに現在割り当てられているプロシージャ キャッシュのページ数です。 負の値であれば、プロセスが他のプロセスから割り当てられたメモリを解放していることになります。|  
|login_time|**datetime**|クライアント プロセスがサーバーにログインした時刻です。|  
|last_batch|**datetime**|クライアント プロセスがリモート ストアド プロシージャ呼び出しまたは EXECUTE ステートメントを前回実行した時刻です。|  
|ecid|**smallint**|単一プロセスに代わって動作しているサブスレッドを一意に識別するために使用する実行コンテキスト ID です。|  
|open_tran|**smallint**|プロセスの開いているトランザクションの数です。|  
|ステータス|**nchar(30)**|プロセス ID の状態です。 可能な値は次のとおりです。<br /><br /> **休止** =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セッションがリセットされています。<br /><br /> **実行している**= セッションでは、1 つまたは複数のバッチが実行中です。 複数のアクティブな結果セット (MARS) が有効な場合、1 回のセッションで複数のバッチを実行できます。 詳細については、次を参照してください。[複数のアクティブな結果セットの使用 & #40 です。MARS & #41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).<br /><br /> **バック グラウンド**= セッションがデッドロック検出など、バック グラウンド タスクを実行しています。<br /><br /> **ロールバック**= セッションでは、プロセスのトランザクションのロールバックします。<br /><br /> **保留中**=、セッションが使用可能になるワーカー スレッドを待機しています。<br /><br /> **実行可能な**= セッションのタスクはクォンタムの取得を待機中にスケジューラの実行可能キューではします。<br /><br /> **spinloop** = セッションのタスクはスピンロックが解放を待機しています。<br /><br /> **中断**= セッションは、完了する I/O など、イベントを待機しています。|  
|sid|**binary(86)**|ユーザーのグローバル一意識別子 (GUID) です。|  
|hostname|**nchar(128)**|ワークステーションの名前です。|  
|program_name|**nchar(128)**|アプリケーション プログラム名です。|  
|hostprocess|**nchar(10)**|ワークステーションのプロセス ID 番号です。|  
|cmd|**nchar(16)**|現在実行中のコマンドです。|  
|nt_domain|**nchar(128)**|クライアントの Windows ドメイン (Windows 認証を使用している場合)、または信頼関係接続の Windows ドメインです。|  
|nt_username|**nchar(128)**|プロセスの Windows ユーザー名 (Windows 認証を使用している場合)、または信頼関係接続の Windows ユーザー名です。|  
|net_address|**nchar(12)**|各ユーザーのワークステーションにあるネットワーク アダプターに割り当てられている一意識別子です。 ユーザーがログインすると、この識別子が net_address 列に挿入されます。|  
|net_library|**nchar(12)**|クライアントのネットワーク ライブラリが保存される列です。 各クライアント プロセスはネットワーク接続を行います。 ネットワーク接続には関係するネットワーク ライブラリがあり、これによって接続が行われます。|  
|loginame|**nchar(128)**|ログイン名。|  
|context_info|**binary(128)**|SET CONTEXT_INFO ステートメントを使用してバッチに格納されるデータです。|  
|sql_handle|**binary(20)**|現在実行されているバッチまたはオブジェクトを表します。<br /><br /> **注**この値は、オブジェクトのバッチまたはメモリ アドレスから派生します。 使用してこの値が計算されない、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ハッシュ アルゴリズム。|  
|stmt_start|**int**|指定した sql_handle の現在の SQL ステートメントの開始オフセットです。|  
|stmt_end|**int**|指定した sql_handle の現在の SQL ステートメントの終了オフセットです。<br /><br /> -1 = 現在のステートメントは、指定した sql_handle に対して fn_get_sql 関数が返す結果の最後まで実行されます。|  
|request_id|**int**|要求の ID です。 特定のセッションで実行されている要求を識別するために使用されます。|  
  
## <a name="remarks"></a>解説  
 インスタンスで実行中のすべてのセッションを表示、サーバーの VIEW SERVER STATE 権限を持つユーザー、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 それ以外の場合、ユーザーが現在のセッションのみを表示します。  
  
## <a name="see-also"></a>参照  
 [実行関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [システム ビューへのシステム テーブルのマッピング&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
