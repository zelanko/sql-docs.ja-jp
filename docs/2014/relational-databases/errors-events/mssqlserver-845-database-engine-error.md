---
title: MSSQLSERVER_845 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 845 (Database Engine error)
ms.assetid: 8fff6ad4-234c-44be-b123-e25d5e1cd63e
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 860fce7c9e8794fce89c76c7f6abb51a1a6773d2
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421011"
---
# <a name="mssqlserver845"></a>MSSQLSERVER_845
    
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
 プロセスがラッチを獲得しようと待機していましたが、待機中に制限時間に達し、獲得に失敗しました。 このエラーは、I/O 操作の完了までに時間がかかりすぎる場合に発生する可能性があります。通常は、他のタスクによってシステムのプロセスが中断された結果のエラーです。 場合によっては、ハードウェア障害によってこのエラーが生じることもあります。  
  
## <a name="user-action"></a>ユーザーの操作  
 次のタスクを実行すると、このエラーを回避できる場合があります。  
  
-   ワークロードを軽減します。  
  
-   エラー ログまたはイベント ログで、関連する I/O エラーがあるかどうか確認します。 通常、I/O エラーはディスクの障害によって発生します。  
  
-   エラー ログで、応答していないタスクや他の重大なエラーがないか調べます。  
  
-   アサートなどの重大なエラーが頻繁に発生する場合は、その問題を解決します。  
  
 エラーが継続して発生する場合は、マイクロソフト カスタマー サービスおよびサポートに問い合わせてください。  
  
  
