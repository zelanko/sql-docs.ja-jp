---
title: LOCALDB_ERROR_INSTANCE_BUSY |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: 0ed9d0f8-3297-4e31-a3e9-4a827f381789
author: stevestein
ms.author: sstein
ms.openlocfilehash: e8f5eb6960a38b9aefc211530a1c29c0ccf8ae69
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87246138"
---
# <a name="localdb_error_instance_busy"></a>LOCALDB_ERROR_INSTANCE_BUSY
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
## <a name="details"></a>詳細  
  
| 属性 | 値 |
| --------- | ----- |
|製品名|SQL Server|  
|イベント ID|274|  
|イベント ソース|SQL Server Local Database Runtime 12.0|  
|コンポーネント|Local Database Runtime API|  
|メッセージ テキスト|ローカル データベース インスタンスで要求された操作は、指定されたインスタンスが現在使用中であるため実行できません。 インスタンスを停止して、再度実行してください。|  
  
## <a name="explanation"></a>説明  
 指定したインスタンスは実行中です。  
  
## <a name="user-action"></a>ユーザーの操作  
 指定した Local Database Runtime インスタンスを停止して、再度実行してください。  
  
  
