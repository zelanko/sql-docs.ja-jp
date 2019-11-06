---
title: sys.sysprocesses (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 60f4cf3945ed026a311e8e8dc0ab37f95ec8aabb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67986498"
---
# <a name="syssysprocesses-transact-sql"></a>sys.sysprocesses (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  インスタンスで実行されているプロセスに関する情報を含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 これらのプロセスには、クライアント側のプロセスまたはシステム プロセスを指定できます。 sysprocesses にアクセスするには、master データベースのコンテキストからアクセスするか、3 つの要素から成る名前 (master.dbo.sysprocesses) を使用する必要があります。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|spid|**smallint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セッション id です。|  
|kpid|**smallint**|Windows スレッド id です。|  
|ブロックされています。|**smallint**|要求をブロックしているセッションの ID。 この列が NULL の場合は、要求がブロックされていないか、ブロックしているセッションのセッション情報が使用または識別できません。<br /><br /> -2 = ブロックしているリソースは、孤立した分散トランザクションが所有しています。<br /><br /> -3 ブロック = 遅延復旧トランザクションが所有するリソースです。<br /><br /> -4 セッション ID を = ブロックしているラッチの所有者が指定されていません内部ラッチの状態遷移が発生したためです。|  
|waittype|**binary(2)**|予約済み。|  
|waittime|**bigint**|現在の待機時間 (ミリ秒単位) です。<br /><br /> 0 = プロセスは待機していません。|  
|lastwaittype|**nchar(32)**|待機の種類を最後または現在の名前を示す文字列。|  
|waitresource|**nchar(256)**|ロック リソースのテキスト表現。|  
|dbid|**smallint**|プロセスによって現在使用されているデータベースの ID。|  
|uid|**smallint**|コマンドを実行したユーザーの ID。 オーバーフローまたはユーザーおよびロールの数が 32,767 を超える場合は NULL を返します。|  
|cpu|**int**|プロセスの累積 CPU 時間。 エントリは、SET STATISTICS TIME オプションが ON であるかどうか、または無効に関係なくすべてのプロセスについて更新されます。|  
|physical_io|**bigint**|累積的なディスクは、プロセスの読み書きします。|  
|memusage|**int**|このプロセスに現在割り当てられているプロシージャ キャッシュ内のページの数。 負の数は、プロセスが別のプロセスによって割り当てられたメモリを解放することを示します。|  
|login_time|**datetime**|クライアント プロセスがサーバーに記録時刻。|  
|last_batch|**datetime**|最後に、クライアント プロセスには、リモート ストアド プロシージャ呼び出しまたは EXECUTE ステートメントが実行されます。|  
|ecid|**smallint**|実行コンテキスト ID が 1 つのプロセスに代わって動作しているサブスレッドを一意に識別するために使用します。|  
|open_tran|**smallint**|プロセスの開いているトランザクションの数。|  
|status|**nchar(30)**|プロセス ID の状態。 設定できる値は次のとおりです。<br /><br /> **休止** =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セッションがリセットされています。<br /><br /> **実行している**= セッションでは、1 つまたは複数のバッチが実行中です。 複数のアクティブな結果セット (MARS) が有効にすると、セッションは、複数のバッチを実行できます。 詳細については、「[複数のアクティブな結果セット &#40;MARS&#41; の使用](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md)」を参照してください。<br /><br /> **バック グラウンド**= セッションはデッドロック検出などのバック グラウンド タスクを実行中です。<br /><br /> **ロールバック**= セッションでは、プロセスのトランザクションのロールバックします。<br /><br /> **保留中**=、セッションが使用可能になるワーカー スレッドを待機しています。<br /><br /> **実行可能な**= セッションのタスクはクォンタムの取得を待機中にスケジューラの実行可能キューでです。<br /><br /> **spinloop** = 無料スピンロックのセッションのタスクが待機しています。<br /><br /> **中断**= セッションは、完了する I/O など、イベントを待機しています。|  
|sid|**binary(86)**|ユーザーのグローバル一意識別子 (GUID)。|  
|hostname|**nchar(128)**|ワークステーションの名前。|  
|program_name|**nchar(128)**|アプリケーション プログラム名です。|  
|hostprocess|**nchar(10)**|ワークステーションのプロセス ID 番号。|  
|cmd|**nchar(16)**|現在実行中のコマンドです。|  
|nt_domain|**nchar(128)**|Windows 認証、または信頼関係接続を使用する場合、クライアントの Windows ドメイン。|  
|nt_username|**nchar(128)**|Windows 認証、または信頼関係接続を使用する場合に、プロセスの Windows ユーザー名。|  
|net_address|**nchar(12)**|各ユーザーのワークステーションにあるネットワーク アダプターに割り当てられている一意識別子です。 ユーザーのログオン、この識別子が net_address 列に挿入されます。|  
|net_library|**nchar(12)**|クライアントのネットワーク ライブラリが格納されている列。 各クライアント プロセスはネットワーク接続を行います。 ネットワーク接続には、それらに関連付けられている接続を作成できるようにするネットワーク ライブラリがあります。|  
|loginame|**nchar(128)**|ログイン名です。|  
|context_info|**binary(128)**|SET CONTEXT_INFO ステートメントを使用してバッチに格納されているデータ。|  
|sql_handle|**binary(20)**|現在実行されているバッチまたはオブジェクトを表します。<br /><br /> **注**この値は、オブジェクトのバッチまたはメモリ アドレスから派生します。 この値を使用して計算されない、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ハッシュ アルゴリズム。|  
|stmt_start|**int**|指定した sql_handle の現在の SQL ステートメントの開始オフセット。|  
|stmt_end|**int**|指定した sql_handle の現在の SQL ステートメントの終了オフセットです。<br /><br /> -1 = 現在のステートメントは、指定した sql_handle に対して fn_get_sql 関数が返す結果の最後まで実行されます。|  
|request_id|**int**|要求の ID。 特定のセッションで実行されている要求を識別するために使用されます。|
|page_resource |**binary(8)** |**適用対象**: [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)] <br /><br /> 8 バイトの 16 進数表現ページ リソースの場合、`waitresource`列には、ページが含まれています。 |  
  
## <a name="remarks"></a>コメント  
 インスタンスで実行中のすべてのセッションを表示、サーバーの VIEW SERVER STATE 権限を持つユーザー、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 そうしないと、現在のセッションのみが表示されます。  
  
## <a name="see-also"></a>関連項目  
 [実行関連の動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [システム ビューへのシステム テーブルのマッピング&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
