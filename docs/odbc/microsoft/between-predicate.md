---
title: "述語の間で |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BETWEEN predicate [ODBC]
- SQL grammar [ODBC], between predicate
ms.assetid: 0cc7464b-d788-4720-98d8-411e1169185f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e8daaa0e1c26f00acbff2e6f7788eab8ee5ac8ce
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="between-predicate"></a>述語の間
構文:  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 唯一場合は true を返します*expression1*がより大きいまたは等しい*expression2*と*expression1*と同じかそれよりも少ない*expression3*.  
  
 この構文のセマンティクスは、デスクトップ データベース ドライバーと Microsoft Jet エンジンで異なります。 Microsoft Jet sql *expression2*よりも大きくすることは*expression3*ステートメントは、場合にのみ、TRUE が返されるように*expression1* 以上*expression3*、および*expression1*と同じかそれよりも少ない*expression2*です。
