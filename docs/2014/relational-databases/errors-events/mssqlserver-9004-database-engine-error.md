---
title: MSSQLSERVER_9004 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 54a5b9a70fee2e85c4057f70f22e1b38a5d39354
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62761850"
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
  
