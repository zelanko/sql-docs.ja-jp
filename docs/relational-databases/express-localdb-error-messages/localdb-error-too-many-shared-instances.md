---
title: LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c1595263-6264-4a43-9535-5eb76ece3a57
author: stevestein
ms.author: sstein
ms.openlocfilehash: 48308ffe551f55b5526fccc634ad84747b9bc976
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87245980"
---
# <a name="localdb_error_too_many_shared_instances"></a>LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
## <a name="details"></a>詳細  
  
| 属性 | 値 |
| --------- | ----- |
|製品名|SQL Server|  
|イベント ID|287|  
|イベント ソース|SQL Server Local Database Runtime 12.0|  
|コンポーネント|Local Database Runtime API|  
|メッセージ テキスト|共有インスタンスの数が多すぎるため、一意のユーザー インスタンス名を生成できません。 いくつかの既存の共有インスタンスの共有を解除してください。|  
  
## <a name="explanation"></a>説明  
 共有インスタンスの数が多すぎるため、一意のユーザー インスタンス名を生成できません。  
  
## <a name="user-action"></a>ユーザーの操作  
 1 つ以上の共有 Local Database Runtime インスタンスの共有を解除して、やり直してください。  
  
  
