---
title: MSSQLSERVER_3151 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 3151 (Database Engine error)
ms.assetid: a8657a91-ec75-4649-a09a-21920e0030ff
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3ce19f35c02f1af6fb430eb6d6beb318e7c4b80a
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver3151"></a>MSSQLSERVER_3151
  
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
  

