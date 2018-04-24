---
title: MSSQLSERVER_17883 | Microsoft Docs
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
- 17883 (Database Engine error)
ms.assetid: adaf1c04-e397-4a69-90b8-9353a37277ea
caps.latest.revision: 15
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 61ef7828090bb4992a8475ef7197d61e0a627577
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver17883"></a>MSSQLSERVER_17883
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|17883|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SRV_SCHEDULER_NONYIELDING|  
|メッセージ テキスト|プロセス %ld:%ld:%ld (0x%lx) ワーカー 0x%p が、スケジューラ %ld で応答を停止している可能性があります。 Thread creation time: %I64d. スレッド CPU 概算使用時間: カーネル %I64d ミリ秒、ユーザー %I64d ミリ秒。 プロセスの使用率 %d%%。 システムのアイドル状態 %d%%。 間隔: %I64d ミリ秒。|  
  
## <a name="explanation"></a>説明  
スケジューラで応答を停止しているスレッドに問題が発生している可能性があることを示します。  これは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内のバグが原因で発生するか、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が実行に必要なサイクルを十分に取得していない場合に発生する可能性があります。  スレッドが最終的に応答すると、このエラーは解決します。  
  
## <a name="user-action"></a>ユーザーの操作  
システムの負荷が高すぎる場合は、負荷を軽減してください。それ以外の場合は、マイクロソフト カスタマー サポート サービスに連絡してください。  
  
