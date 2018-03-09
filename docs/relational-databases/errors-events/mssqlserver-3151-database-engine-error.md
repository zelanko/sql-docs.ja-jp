---
title: MSSQLSERVER_3151 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 3151 (Database Engine error)
ms.assetid: a8657a91-ec75-4649-a09a-21920e0030ff
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6619b231e79efa08e43092de66671e27f78b1fd6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver3151"></a>MSSQLSERVER_3151
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|3151|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|LDDB_MASTER_LOAD_FAILED|  
|メッセージ テキスト|master データベースを復元できませんでした。 SQL Server をシャットダウンしています。 エラー ログを確認し、master データベースを再構築してください。 master データベースを再構築する方法の詳細については、SQL Server オンライン ブックを参照してください。|  
  
## <a name="explanation"></a>説明  
これは一般エラー メッセージであり、**master** データベースに関するさまざまな問題を示しています。  
  
## <a name="user-action"></a>ユーザーの操作  
詳細については、エラー ログを確認してください。 使用可能な **master** データベースを作成するには、REBUILDDATABASE オプションを使用して Setup.exe を実行します。 詳細については、SQL Server オンライン ブックの「コマンド プロンプトから SQL Server をインストールする方法」を参照してください。  
  
