---
title: LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c178a308-8d99-47fc-8a49-5a480dc592f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: a5bef5b71095d0cc23cf76cc822780c88a290baf
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87246057"
---
# <a name="localdb_error_instance_folder_path_too_long"></a>LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
## <a name="details"></a>詳細  
  
| 属性 | 値 |
| --------- | ----- | 
|製品名|SQL Server|  
|イベント ID|260|  
|イベント ソース|SQL Server Local Database Runtime 12.0|  
|コンポーネント|Local Database Runtime API|  
|メッセージ テキスト|ローカル データベース インスタンス フォルダーの完全なパスの長さが MAX_PATH よりも長くなっています。 インスタンスは、次のフォルダーに格納されている必要があります:%% LOCALAPPDATA%% \ Microsoft\Microsoft SQL Server ローカル Db\ インスタンス \\<インスタンス名 \> 。|  
  
## <a name="explanation"></a>説明  
 インスタンスを格納するパスの長さが MAX_PATH を超過しています。  
  
## <a name="user-action"></a>ユーザーの操作  
 MAX_PATH よりも短い新しいパスを作成してください。  
  
  
