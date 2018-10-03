---
title: LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: reference
ms.assetid: c1595263-6264-4a43-9535-5eb76ece3a57
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 676a827d1d930d870e2441e7b870c70eabc6652e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48089012"
---
# <a name="localdberrortoomanysharedinstances"></a>LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES
    
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
  
  
