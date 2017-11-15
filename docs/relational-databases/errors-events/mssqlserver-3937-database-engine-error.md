---
title: MSSQLSERVER_3937 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 3937 (Database Engine error)
ms.assetid: 312d5bbe-c8de-42db-af4b-4ccb448ce6ef
caps.latest.revision: "12"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 113385d8dd09b70f4d058fb24a113f7065866eeb
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver3937"></a>MSSQLSERVER_3937
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|MSSQLSERVER|  
|イベント ID|3937|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|XACT_FILESTREAM_ROLLBACK_ERROR|  
|メッセージ テキスト|ファイル ストリーム フィルター ドライバーに、トランザクションがロールバックされたことを通知しようとして、エラーが発生しました。 エラー コード: 0x%0x。|  
  
## <a name="explanation"></a>説明  
トランザクションのロールバック通知の発行時に、RsFx ドライバーからエラーが返されました。 これは、リソース不足が原因である可能性があります。 これにより、RsFx フィルター ドライバーで小規模なメモリ リークが発生する場合があります。ただし、このメモリ リークはトランザクションを作成した sqlservr.exe プロセスの終了時に解放されます。  
  
## <a name="user-action"></a>ユーザーの操作  
