---
title: MSSQLSERVER_3413 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3413 (Database Engine error)
ms.assetid: 3fa07637-ba93-4633-aaf2-ade7d18bc487
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2af9a604c511c50b542fbacd547afb3e09d7ea54
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62868372"
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
  
