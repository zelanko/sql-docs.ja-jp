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
manager: craigg
ms.openlocfilehash: 57d05a00a157a8e5bffec8720a4c8e0716a802f6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63062380"
---
# <a name="localdberrorcallerisnotowner"></a>LOCALDB_ERROR_CALLER_IS_NOT_OWNER
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
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
  
  
