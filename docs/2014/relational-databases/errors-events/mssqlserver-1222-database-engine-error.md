---
title: MSSQLSERVER_1222 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 1222 (Database Engine error)
ms.assetid: c5b1c2f4-f591-4cc1-aa17-204636a27f29
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 850d4bc168be2cbbf602b3fc6ebb4e317245de7c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083915"
---
# <a name="mssqlserver1222"></a>MSSQLSERVER_1222
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|1222|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|LK_TIMEOUT|  
|メッセージ テキスト|ロック要求がタイムアウトしました。|  
  
## <a name="explanation"></a>説明  
 必要なリソースが、このクエリが待機できる時間より長く別のトランザクションによって拘束されています。  
  
## <a name="user-action"></a>ユーザーの操作  
 問題を軽減するには、次の操作を行います。  
  
1.  可能であれば、必要なリソースのロックを保持しているトランザクションを探します。 **sys.dm_os_waiting_tasks** および **sys.dm_tran_locks** 動的管理ビューを使用してください。  
  
2.  トランザクションがロックをまだ保持している場合は、必要に応じてこのトランザクションを中止します。  
  
3.  クエリを再実行します。  
  
 このエラーが頻繁に発生する場合は、ロック要求のタイムアウト時間を変更するか、原因となっているトランザクションを修正してロックの拘束時間を短くします。  
  
  