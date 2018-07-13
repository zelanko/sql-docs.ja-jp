---
title: MSSQL_ENG014152 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014152 error
ms.assetid: 4215e2b1-cd30-441f-9671-9afc742adf6e
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4b499d24a6cfa7c09f75d0d0150eb8f2f942d4b7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37205222"
---
# <a name="mssqleng014152"></a>MSSQL_ENG014152
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|14152|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|レプリケーション-%s: エージェント %s には再試行のスケジュールが設定されました。 %s|  
  
## <a name="explanation"></a>説明  
 指定されたレプリケーション エージェントは、要求された操作を再試行するようにスケジュール設定されました。 ジョブ ステップに設定された再試行の最大回数に達するまで、このプロセスが繰り返し再試行されます。  
  
 通常、再試行は次のいずれかの理由により発生します。  
  
-   **QueryTimeout** 値を超過する。  
  
-   **LoginTimeout** 値を超過する。  
  
-   レプリケーション プロセスがデッドロックの対象として選択される。  
  
## <a name="user-action"></a>ユーザーの操作  
 この再試行のメッセージの発生頻度が低い場合、ユーザー操作は不要です。  
  
 [sp_help_jobstep](/sql/relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql) を使用して、指定されたレプリケーション エージェントの **[エージェントを実行します。]** ステップが再試行される最大回数の現在の設定を表示します。 [sp_update_jobstep](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql) ストアド プロシージャの **@retry_attempts** パラメーターを使用して、ジョブ ステップが再試行される回数を調整することができます。  
  
 再試行のメッセージが頻繁に表示される場合は、再試行が発生するメッセージに基づく問題のトラブルシューティングを行います。 エージェントの履歴で、再試行をスケジュール設定する必要があった理由を示すメッセージを確認します。 場合によっては、レプリケーション エージェントに対してより詳細なログ記録を有効にする必要があります。 レプリケーションのログ記録を構成する方法については、サポート技術情報の資料 [312292](http://support.microsoft.com/kb/312292)を参照してください。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md)  
  
  
