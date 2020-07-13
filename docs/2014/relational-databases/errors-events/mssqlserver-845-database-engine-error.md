---
title: MSSQLSERVER_845 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 845 (Database Engine error)
ms.assetid: 8fff6ad4-234c-44be-b123-e25d5e1cd63e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ff19f2b2e57d1b7c29b2aefe69e8ba4cae5c58dd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85053596"
---
# <a name="mssqlserver_845"></a>MSSQLSERVER_845
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|845|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|BUFLATCH_TIMEOUT|  
|メッセージ テキスト|バッファー ラッチを待機中にタイムアウトが発生しました。ページ %S_PGID の型 %d、データベース ID %d。|  
  
## <a name="explanation"></a>説明  
 ラッチを取得するためにプロセスが待機中でしたが、制限時間に達したため、取得できませんでした。 このエラーは、I/O 操作の完了までに時間がかかりすぎる場合に発生する可能性があります。通常は、他のタスクによってシステムのプロセスが中断された結果のエラーです。 場合によっては、ハードウェア障害によってこのエラーが生じることもあります。  
  
## <a name="user-action"></a>ユーザーの操作  
 次のタスクを実行すると、このエラーを回避できる場合があります。  
  
-   ワークロードを軽減します。  
  
-   エラー ログまたはイベント ログで、関連する I/O エラーがあるかどうか確認します。 通常、I/O エラーはディスクの障害によって発生します。  
  
-   エラー ログで、応答していないタスクや他の重大なエラーがないか調べます。  
  
-   アサートなどの重大なエラーが頻繁に発生する場合は、その問題を解決します。  
  
 エラーが継続して発生する場合は、マイクロソフト カスタマー サービスおよびサポートに問い合わせてください。  
  
  
