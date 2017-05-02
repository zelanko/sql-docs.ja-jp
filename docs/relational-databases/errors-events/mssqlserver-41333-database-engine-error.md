---
title: MSSQLSERVER_41333 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 41333 (Database Engine error)
ms.assetid: c3c3ae9a-1e4c-4de6-ba72-2f393375b053
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 72f5461f4e60b7e4c5cb53df75906d1aae0a07a5
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver41333"></a>MSSQLSERVER_41333
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|41333|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|CROSS_CONTAINER_ISOLATION_FAILURE|  
|メッセージ テキスト|RepeatableRead トランザクション、Serializable トランザクション、および RepeatableRead または Serializable 分離でメモリ最適化されていないテーブルにアクセスするトランザクションでは、スナップショット分離を使用したうえでメモリ最適化テーブルおよびネイティブ コンパイル ストアド プロシージャにアクセスする必要があります。|  
  
## <a name="explanation"></a>説明  
ディスク ベース トランザクションと XTP トランザクションの間の分離レベルが高いユーザーに対しては、制約があります。  
  
## <a name="user-action"></a>ユーザーの操作  
メモリ最適化テーブル (およびネイティブ コンパイル プロシージャ) とディスク ベース テーブルでは、高レベルの分離操作を実行しないでください。  
  
詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[インメモリ OLTP &#40;インメモリ最適化&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

