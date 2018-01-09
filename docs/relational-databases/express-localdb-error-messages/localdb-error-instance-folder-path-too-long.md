---
title: "LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: localdb
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c178a308-8d99-47fc-8a49-5a480dc592f6
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3ae486a71a93653345a1e852246f32ee5e856e15
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="localdberrorinstancefolderpathtoolong"></a>LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|260|  
|イベント ソース|SQL Server Local Database Runtime 12.0|  
|コンポーネント|Local Database Runtime API|  
|メッセージ テキスト|ローカル データベース インスタンス フォルダーの完全なパスの長さが MAX_PATH よりも長くなっています。 インスタンスは、フォルダーに格納する必要があります: %%LOCALAPPDATA%%\Microsoft\Microsoft SQL Server のローカル DB\Instances\\< インスタンス名\>です。|  
  
## <a name="explanation"></a>説明  
 インスタンスを格納するパスの長さが MAX_PATH を超過しています。  
  
## <a name="user-action"></a>ユーザーの操作  
 MAX_PATH よりも短い新しいパスを作成してください。  
  
  
