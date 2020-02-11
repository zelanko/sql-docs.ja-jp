---
title: 管理ツール コマンド ライン オプション (分散再生ユーティリティ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: c01b0ed3-67e4-4561-92d2-a8fbb086aca8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f53c456832e89aa96c0f7c9a1decd9fabbe96360
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63151579"
---
# <a name="administration-tool-command-line-options-distributed-replay-utility"></a>管理ツール コマンド ライン オプション (Distributed Replay Utility)
  分散再生管理ツール`DReplay.exe`は、分散再生コントローラーとの通信に使用できるコマンドラインツールです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理ツールを使用して、コントローラー上の操作を開始、監視、取り消しできます。  
  
 ![トピックリンクアイコン](../../database-engine/media/topic-link.gif "トピック リンク アイコン")管理ツールの構文で使用される構文表記規則の詳細については、「transact-sql[構文表記規則 &#40;transact-sql&#41;](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
      dreplay {preprocess|replay|status|cancel} [options] [-?]}  
  
Usage:  
  
  dreplay preprocess [-mcontroller] -iinput_trace_file  
    -dcontroller_working_dir [-cconfig_file] [-fstatus_interval]  
  
  dreplay replay [-mcontroller] -dcontroller_working_dir [-o]  
    [-starget_server] -wclients [-cconfig_file]  
    [-fstatus_interval]  
  
  dreplay status [-mcontroller] [-fstatus_interval]  
  
  dreplay cancel [-mcontroller] [-q]   
```  
  
## <a name="remarks"></a>解説  
 
  `DReplay.exe` では、次のコマンド ライン オプションを発行することができます。  
  
 **在庫**  
 前処理段階を開始します。 コントローラーは、ターゲット サーバーに対する再生のために、運用環境からキャプチャした入力トレース データの準備を行います。  
  
 **反射**  
 イベント再生段階を開始します。 コントローラーは、指定されたクライアントに再生データをディスパッチし、分散再生を開始して、クライアントを同期します。 必要に応じて、選択された各クライアントは、再生アクティビティを記録し、結果トレース ファイルをローカルに保存します。  
  
 **オンライン**  
 コントローラーにクエリし、現在の状態を表示します。  
  
 **キャンセル**  
 コントローラーで実行されている現在の操作を取り消します。  
  
 コマンドの引数や例などの構文情報の詳細については、次のトピックを参照してください。  
  
-   [前処理オプション &#40;分散再生管理ツール&#41;](preprocess-option-distributed-replay-administration-tool.md)  
  
-   [再生オプション &#40;分散再生管理ツール&#41;](replay-option-distributed-replay-administration-tool.md)  
  
-   [[状態] オプション &#40;分散再生管理ツール&#41;](status-option-distributed-replay-administration-tool.md)  
  
-   [[キャンセル] オプション &#40;分散再生管理ツール&#41;](cancel-option-distributed-replay-administration-tool.md)  
  
 RPC は、言語イベントとしてではなく RPC として再生されます。  
  
## <a name="permissions"></a>アクセス許可  
 対話ユーザー (ローカル ユーザーまたはドメイン ユーザー アカウント) として、管理ツールを実行する必要があります。 ローカル ユーザー アカウントを使用するには、管理ツールとコントローラーが同じコンピューター上で実行されている必要があります。  
  
 詳細については、「 [Distributed Replay Security](distributed-replay-security.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server Distributed Replay](sql-server-distributed-replay.md)  
  
  
