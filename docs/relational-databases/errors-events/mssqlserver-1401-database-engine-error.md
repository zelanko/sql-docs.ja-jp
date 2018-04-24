---
title: MSSQLSERVER_1401 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 1401 (Database Engine error)
ms.assetid: 02928770-aa63-4509-8713-406c73e4cedc
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8d30bfa0a55fcf15c5027f4fd7dcdceaf9c22d55
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver1401"></a>MSSQLSERVER_1401
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|1401|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBM_MASTERSTARTUP|  
|メッセージ テキスト|データベース ミラーリングのマスター スレッド ルーチンのスタートアップが次の理由により失敗しました: %ls。 このエラーの原因を解決して SQL Server サービスを再開してください。|  
  
## <a name="explanation"></a>説明  
ミラーリングを制御するスレッドのスタートアップに失敗しました。  
  
## <a name="user-action"></a>ユーザーの操作  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログを調べ、このメッセージの前に関連するエラーが記録されているかどうかを確認します。 このエラーの原因を解決したら、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス (MSSQLSERVER) を再開します。  
  
## <a name="see-also"></a>参照  
[データベース エンジン、SQL Server エージェント、SQL Server Browser サービスの開始、停止、一時停止、再開、および再起動](~/database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
