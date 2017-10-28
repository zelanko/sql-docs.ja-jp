---
title: "[SQL Server エージェントのプロパティ]([履歴] ページ) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.ag.agent.history.f1
ms.assetid: dc73734c-b3c3-407f-bbd1-8714b4fa47b0
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 51839ab3d459e2350c582810fe003fc5086de3eb
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-agent-properties-history-page"></a>[SQL Server エージェントのプロパティ] \([履歴] ページ)
このページを使用すると、[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェント サービス履歴ログの管理設定の表示と設定を行うことができます。  
  
## <a name="options"></a>オプション  
**[ジョブ履歴ログのサイズを制限する]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントがログで保持するジョブ履歴情報のサイズの上限を設定します。  
  
**[ジョブ履歴ログの最大サイズ (行)]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントによって保持される行の最大数を設定します。 ログの大きさがここで設定した行数に達すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントは新しい行を入力するときにログの最も古い行を削除します。  
  
**[ジョブごとのジョブ履歴の最大行数]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントによってジョブごとに保持される行の最大数を設定します。 特定のジョブの履歴サイズがここで設定した行数に達すると、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントは新しい行を入力するときにログの最も古い行を削除します。  
  
**[エージェントの履歴を削除する]**  
ログ内のエントリの保存期間が指定された期間を超えたときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントがそのエントリを削除するように指定します。 これは、履歴を削除するために、1 回だけ実行されます。 繰り返し実行する必要がある場合は、クリーンアップ ジョブのメンテナンス プランを作成してスケジュールします。  
  
**[経過期間]**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントがエントリを保持する期間を設定します。  
  
## <a name="see-also"></a>参照  
[SQL Server エージェント エラー ログ](../../ssms/agent/sql-server-agent-error-log.md)  
  

