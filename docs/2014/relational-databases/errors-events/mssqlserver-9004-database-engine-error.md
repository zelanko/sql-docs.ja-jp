---
title: MSSQLSERVER_9004 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 08cf49c351df3b1130fea55e2d34f7fa7bcbd890
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86550783"
---
# <a name="mssqlserver_9004"></a>MSSQLSERVER_9004
    
## <a name="details"></a>詳細  
  
|属性|値|  
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
  
  
