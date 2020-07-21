---
title: LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c1595263-6264-4a43-9535-5eb76ece3a57
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0896f3e70e6c65a1fcd0de4169249fb622e6b5f8
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85051082"
---
# <a name="localdb_error_too_many_shared_instances"></a>LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|287|  
|イベント ソース|SQL Server Local Database Runtime 12.0|  
|コンポーネント|Local Database Runtime API|  
|メッセージ テキスト|共有インスタンスの数が多すぎるため、一意のユーザー インスタンス名を生成できません。 いくつかの既存の共有インスタンスの共有を解除してください。|  
  
## <a name="explanation"></a>説明  
 共有インスタンスの数が多すぎるため、一意のユーザー インスタンス名を生成できません。  
  
## <a name="user-action"></a>ユーザーの操作  
 1 つ以上の共有 Local Database Runtime インスタンスの共有を解除して、やり直してください。  
  
  
