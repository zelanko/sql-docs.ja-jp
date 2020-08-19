---
description: MSSQLSERVER_845
title: MSSQLSERVER_845 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 845 (Database Engine error)
ms.assetid: 8fff6ad4-234c-44be-b123-e25d5e1cd63e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 621699cbc4ad763eea84669e085ea492eb6a546f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88420916"
---
# <a name="mssqlserver_845"></a>MSSQLSERVER_845
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
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
  
