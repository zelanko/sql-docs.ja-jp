---
title: MSSQLSERVER_9004 | Microsoft Docs
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
- 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
caps.latest.revision: 16
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6d2d5cefa8aa83b92f589d939f1c7c53b23b3f1f
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver9004"></a>MSSQLSERVER_9004
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  

