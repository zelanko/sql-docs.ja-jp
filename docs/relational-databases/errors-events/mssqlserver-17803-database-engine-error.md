---
title: MSSQLSERVER_17803 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 17803 (Database Engine error)
ms.assetid: 28591a19-258d-4891-b78a-4686789bb2d7
caps.latest.revision: "14"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 683a66793d0755d31469b09434090c87e931cbec
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver17803"></a>MSSQLSERVER_17803
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|17803|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SRV_NOMEMORY|  
|メッセージ テキスト|接続の確立中にメモリの割り当てエラーが発生しました。 不要なメモリ負荷を減らすか、システム メモリを増やしてください。 接続が閉じられました。%.*ls|  
  
## <a name="explanation"></a>説明  
サーバーのメモリが不足しています。  
  
## <a name="user-action"></a>ユーザーの操作  
サーバーのメモリが不足している原因を特定してください。 一般的なメモリのトラブルシューティング手順を使用できます。  
  
