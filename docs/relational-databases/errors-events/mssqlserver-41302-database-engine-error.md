---
title: MSSQLSERVER_41302 | Microsoft Docs
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
- 41302 (Database Engine error)
ms.assetid: 01e75618-afec-4232-ba68-93ab7bc31003
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 82590136989c70ec171c06ae6a8f1dcc6d919a61
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver41302"></a>MSSQLSERVER_41302
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|41302|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|WRITE_WRITE_CONFLICT|  
|メッセージ テキスト|現在のトランザクションが、このトランザクションが開始してから更新されたレコードを更新しようとしました。 トランザクションは中止されました。|  
  
## <a name="explanation"></a>説明  
トランザクションで書き込み/書き込みの競合が発生したため、ステートメントが終了しました。  
  
## <a name="user-action"></a>ユーザーの操作  
別のトランザクションで、後で操作を再試行してください。 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[インメモリ OLTP &#40;インメモリ最適化&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

