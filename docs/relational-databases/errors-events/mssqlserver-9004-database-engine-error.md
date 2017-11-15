---
title: MSSQLSERVER_9004 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 8c794316e9995e4a61fd0af55318c411dbcbda61
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver9004"></a>MSSQLSERVER_9004
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|9004|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|LOG_CORRUPT|  
|メッセージ テキスト|データベース '%.*ls' のログを処理中にエラーが発生しました。  可能な場合は、バックアップから復元してください。 バックアップを使用できない場合は、ログの再構築が必要になることがあります。|  
  
## <a name="explanation"></a>説明  
ロールバック、復旧、またはレプリケーションの操作で、ログの処理中にエラーが発生しました。 オペレーティング システムで検出されたエラーか、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で検出された内部的な一貫性エラーを示している可能性があります。  
  
## <a name="user-action"></a>ユーザーの操作  
次のいずれかのアクションでこのエラーを修正します。  
  
-   バックアップからの復元を実行する。  
  
-   ログを再構築する。  
  
また、システムのイベント ログまたはエラー ログで、システム内の問題がエラーの原因になっていないか調べます。  
  
