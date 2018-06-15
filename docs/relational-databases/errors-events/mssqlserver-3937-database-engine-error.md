---
title: MSSQLSERVER_3937 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 3937 (Database Engine error)
ms.assetid: 312d5bbe-c8de-42db-af4b-4ccb448ce6ef
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 263747514a29b61f82b308078decbe2967c6fb6b
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
ms.locfileid: "34319903"
---
# <a name="mssqlserver3937"></a>MSSQLSERVER_3937
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
