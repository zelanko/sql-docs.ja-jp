---
title: "述語の間で |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BETWEEN predicate [ODBC]
- SQL grammar [ODBC], between predicate
ms.assetid: 0cc7464b-d788-4720-98d8-411e1169185f
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1738aa33f371a2e64ea0362cefcf59a759fdfee7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="between-predicate"></a>述語の間
構文:  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 唯一場合は true を返します*expression1*がより大きいまたは等しい*expression2*と*expression1*と同じかそれよりも少ない*expression3*.  
  
 この構文のセマンティクスは、デスクトップ データベース ドライバーと Microsoft Jet エンジンで異なります。 Microsoft Jet sql *expression2*よりも大きくすることは*expression3*ステートメントは、場合にのみ、TRUE が返されるように*expression1* 以上*expression3*、および*expression1*と同じかそれよりも少ない*expression2*です。
