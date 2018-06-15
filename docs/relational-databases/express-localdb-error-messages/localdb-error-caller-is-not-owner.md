---
title: LOCALDB_ERROR_CALLER_IS_NOT_OWNER |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: performance
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f3303072-2b44-4443-936c-f024b0b2a8c5
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8fb1c49335d9fbd25d0e4518e181913ff5eaa33f
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
ms.locfileid: "34324903"
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
  
  
