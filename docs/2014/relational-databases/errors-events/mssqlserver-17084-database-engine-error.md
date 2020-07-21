---
title: MSSQLSERVER_17084 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17084 (Database Engine error)
ms.assetid: e579d104-3307-4edd-8587-b14ecbc02ed9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f410856e3be5f7d80acda994cc7eab0ad8e477be
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553687"
---
# <a name="mssqlserver_17084"></a>MSSQLSERVER_17084
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|17084|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|P3_ATOMIC_WITH_MISSING_OPTION|  
|メッセージ テキスト|BEGIN ATOMIC ステートメントの WITH 句は、オプション '%ls' の値を指定する必要があります。|  
  
## <a name="explanation"></a>説明  
 BEGIN ATOMIC ステートメントの WITH 句で、オプションの値が指定されませんでした。  
  
## <a name="user-action"></a>ユーザーの操作  
 `ATOMIC` ブロックでは、`WITH` オプションの `TRANSACTION ISOLATION LEVEL` および `LANGUAGE` に値が必要です。 次に例を示します。  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE= N'us_english')  
```  
  
 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP &#40;インメモリ最適化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
