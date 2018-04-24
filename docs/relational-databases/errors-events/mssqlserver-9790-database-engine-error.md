---
title: MSSQLSERVER_9790 | Microsoft Docs
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
- 9790 (Database Engine error)
ms.assetid: 83fd379f-5deb-4f97-8cb4-282e3d3fed94
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 27f8ec87871d65f93aec1ed4c4914e3c7511fb56
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver9790"></a>MSSQLSERVER_9790
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|9790|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER|  
|メッセージ テキスト|着信メッセージをルーティングできません。 ルーティング情報を保持するシステム データベース MSDB がシングル ユーザー モードです。|  
  
## <a name="explanation"></a>説明  
MSDB データベースがシングル ユーザー モードであったため、外部から受信したメッセージを分類しようとしたときにエラーが発生しました。  
  
## <a name="user-action"></a>ユーザーの操作  
ALTER DATABASE コマンドを使用して、MSDB をマルチ ユーザー モードに変更します。  
  
