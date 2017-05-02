---
title: MSSQL_ENG014152 | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG014152 error
ms.assetid: 4215e2b1-cd30-441f-9671-9afc742adf6e
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 06008fe3c31133feab100628a7f0e813acefa17c
ms.lasthandoff: 04/11/2017

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
  
 [sp_help_jobstep](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md) を使用して、指定されたレプリケーション エージェントの **[エージェントを実行します。]** ステップが再試行される最大回数の現在の設定を表示します。 [sp_update_jobstep](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md) ストアド プロシージャの **@retry_attempts** パラメーターを使用して、ジョブ ステップが再試行される回数を調整することができます。  
  
 再試行のメッセージが頻繁に表示される場合は、再試行が発生するメッセージに基づく問題のトラブルシューティングを行います。 エージェントの履歴で、再試行をスケジュール設定する必要があった理由を示すメッセージを確認します。 場合によっては、レプリケーション エージェントに対してより詳細なログ記録を有効にする必要があります。 レプリケーションのログ記録を構成する方法については、サポート技術情報の資料 [312292](http://support.microsoft.com/kb/312292)を参照してください。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
