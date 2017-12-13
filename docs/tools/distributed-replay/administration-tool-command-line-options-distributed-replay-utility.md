---
title: "管理ツール コマンド ライン オプション (Distributed Replay Utility) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/12/2016
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: distributed-replay
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c01b0ed3-67e4-4561-92d2-a8fbb086aca8
caps.latest.revision: "35"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ae6edc607f16e822d2b752ee31c94042122007d7
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2017
---
# <a name="administration-tool-command-line-options-distributed-replay-utility"></a>管理ツール コマンド ライン オプション (Distributed Replay Utility)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 管理ツール、 **DReplay.exe**、distributed replay controller と通信するコマンド ライン ツールです。 管理ツールを使用して、コントローラー上の操作を開始、監視、取り消しできます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン")管理ツールの構文で使用される構文表記規則の詳細については、次を参照してください。 [TRANSACT-SQL 構文表記規則 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
dreplay {preprocess|replay|status|cancel} [options] [-?]}  
  
Usage:  
  
  dreplay preprocess [-m controller] -i input_trace_file  
    -d controller_working_dir [-c config_file] [-f status_interval]  
  
  dreplay replay [-m controller] -d controller_working_dir [-o]  
    [-s target_server] -w clients [-c config_file]  
    [-f status_interval]  
  
  dreplay status [-m controller] [-f status_interval]  
  
  dreplay cancel [-m controller] [-q]   
```  
  
## <a name="remarks"></a>解説  
 **DReplay.exe**では、次のコマンド ライン オプションを発行することができます。  
  
 **preprocess**  
 前処理段階を開始します。 コントローラーは、対象サーバーに対する再生のために、運用環境からキャプチャした入力トレース データの準備を行います。  
  
 **再生 (replay)**  
 イベント再生段階を開始します。 コントローラーは、指定されたクライアントに再生データをディスパッチし、分散再生を開始して、クライアントを同期します。 必要に応じて、選択された各クライアントは、再生アクティビティを記録し、結果トレース ファイルをローカルに保存します。  
  
 **ステータス**  
 コントローラーにクエリし、現在の状態を表示します。  
  
 **cancel**  
 コントローラーで実行されている現在の操作を取り消します。  
  
 コマンドの引数や例などの構文情報の詳細については、次のトピックを参照してください。  
  
-   [前処理オプション &#40;Distributed Replay 管理ツール&#41;](../../tools/distributed-replay/preprocess-option-distributed-replay-administration-tool.md)  
  
-   [replay オプション &#40;Distributed Replay 管理ツール&#41;](../../tools/distributed-replay/replay-option-distributed-replay-administration-tool.md)  
  
-   [status オプション &#40;Distributed Replay 管理ツール&#41;](../../tools/distributed-replay/status-option-distributed-replay-administration-tool.md)  
  
-   [cancel オプション &#40;Distributed Replay 管理ツール&#41;](../../tools/distributed-replay/cancel-option-distributed-replay-administration-tool.md)  
  
 RPC は、言語イベントとしてではなく RPC として再生されます。  
  
## <a name="permissions"></a>アクセス許可  
 対話ユーザー (ローカル ユーザーまたはドメイン ユーザー アカウント) として、管理ツールを実行する必要があります。 ローカル ユーザー アカウントを使用するには、管理ツールとコントローラーが同じコンピューター上で実行されている必要があります。  
  
 詳細については、「 [Distributed Replay Security](../../tools/distributed-replay/distributed-replay-security.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)  
  
  
