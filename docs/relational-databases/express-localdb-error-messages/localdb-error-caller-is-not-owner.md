---
title: LOCALDB_ERROR_CALLER_IS_NOT_OWNER |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: f3303072-2b44-4443-936c-f024b0b2a8c5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 949c03aefc35b7ff99320bfbff980210dff092dd
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717690"
---
# <a name="localdb_error_caller_is_not_owner"></a>LOCALDB_ERROR_CALLER_IS_NOT_OWNER
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|282|  
|イベント ソース|SQL Server Local Database Runtime 12.0|  
|コンポーネント|Local Database Runtime API|  
|メッセージ テキスト|API 呼び出し元は、ローカル データベース インスタンスの所有者ではありません。|  
  
## <a name="explanation"></a>説明  
 要求された操作を実行するには、ユーザーがインスタンスの所有者である必要があります。  
  
## <a name="user-action"></a>ユーザーの操作  
 インスタンスの所有者に問い合わせてください。  
  
  
