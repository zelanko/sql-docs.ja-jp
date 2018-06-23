---
title: LOCALDB_ERROR_TOO_MANY_SHARED_INSTANCES |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c1595263-6264-4a43-9535-5eb76ece3a57
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 865b682ec0f2a55d76ac9163da575aa5cbdaf9a4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083200"
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
  
  