---
title: LOCALDB_ERROR_INSUFFICIENT_BUFFER |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: ff67bda8-7e5c-4b06-8d7b-9985b6059a98
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 821966822629240b91c64fe91b3c059b22ff377d
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415821"
---
# <a name="localdberrorinsufficientbuffer"></a>LOCALDB_ERROR_INSUFFICIENT_BUFFER
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|276|  
|イベント ソース|SQL Server Local Database Runtime 12.0|  
|コンポーネント|Local Database Runtime API|  
|メッセージ テキスト|ローカル データベース インスタンスの API メソッドに渡されたバッファーのサイズが不十分です。|  
  
## <a name="explanation"></a>説明  
 入力バッファーが短かすぎますが、切り捨ては要求されませんでした。  
  
## <a name="user-action"></a>ユーザーの操作  
 指定したサイズのバッファーを提供してください。  
  
  
