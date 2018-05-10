---
title: MSSQLSERVER_3413 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 3413 (Database Engine error)
ms.assetid: 3fa07637-ba93-4633-aaf2-ade7d18bc487
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9cfa7a7f5b40767776c0db4ac58918ccf45080f4
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver3413"></a>MSSQLSERVER_3413
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|3413|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|MARKDB|  
|メッセージ テキスト|データベース ID %d。 データベースを問題ありに設定できませんでした。 sys.databases.database_id での Getnext NC スキャンが失敗しました。 エラー ログで以前のエラーを参照して原因を特定し、関連している問題をすべて修正してください。|  
  
## <a name="explanation"></a>説明  
カタログ内で、ユーザー データベースを SUSPECT に設定しようとして、予期しないエラーが発生しました。 SUSPECT 状態は保存されません。  
  
## <a name="user-action"></a>ユーザーの操作  
これより前に発生したエラーを調べて、問題を修正します。  
  
