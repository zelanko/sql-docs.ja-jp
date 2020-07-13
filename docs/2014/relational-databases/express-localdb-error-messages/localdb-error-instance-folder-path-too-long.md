---
title: LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c178a308-8d99-47fc-8a49-5a480dc592f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 32ae8ebe102008d08a6059328ed57cd118ece019
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85051182"
---
# <a name="localdb_error_instance_folder_path_too_long"></a>LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|260|  
|イベント ソース|SQL Server Local Database Runtime 12.0|  
|コンポーネント|Local Database Runtime API|  
|メッセージ テキスト|ローカル データベース インスタンス フォルダーの完全なパスの長さが MAX_PATH よりも長くなっています。 インスタンスは、次のフォルダーに格納されている必要があります:%% LOCALAPPDATA%% \ Microsoft\Microsoft SQL Server ローカル Db\ インスタンス \\<インスタンス名 \> 。|  
  
## <a name="explanation"></a>説明  
 インスタンスを格納するパスの長さが MAX_PATH を超過しています。  
  
## <a name="user-action"></a>ユーザーの操作  
 MAX_PATH よりも短い新しいパスを作成してください。  
  
  
