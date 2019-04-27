---
title: LOCALDB_ERROR_INSTANCE_ALREADY_SHARED |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: 35b4d6fa-ebb9-49d3-aaab-d4e37b6f3760
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5f562a0cbd489202d5dbab7de6ac0d19ebeef348
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62519369"
---
# <a name="localdberrorinstancealreadyshared"></a>LOCALDB_ERROR_INSTANCE_ALREADY_SHARED
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|284|  
|イベント ソース|SQL Server Local Database Runtime 12.0|  
|コンポーネント|Local Database Runtime API|  
|メッセージ テキスト|指定したローカル データベース インスタンスは既に共有されています。|  
  
## <a name="explanation"></a>説明  
 指定したローカル データベース インスタンスは既に別の共有名で共有されています。  
  
## <a name="user-action"></a>ユーザーの操作  
 共有インスタンスを別の共有名で再度共有する前に、そのインスタンスの共有を解除してください。  
  
  
