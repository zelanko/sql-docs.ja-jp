---
title: BETWEEN 述語 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- BETWEEN predicate [ODBC]
- SQL grammar [ODBC], between predicate
ms.assetid: 0cc7464b-d788-4720-98d8-411e1169185f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1a0ac99729966acdcb03c2aab0175c34bba0c08a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138115"
---
# <a name="between-predicate"></a>BETWEEN 述語
構文は次のとおりです。  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 *expression1*が*expression2*以上で*expression1*が*expression3*以下である場合にのみ true を返します。  
  
 この構文のセマンティクスは、デスクトップデータベースドライバーと Microsoft Jet エンジンによって異なります。 Microsoft Jet SQL では、 *expression2*は*expression3*よりも大きくすることができます。 *expression1*が*expression3*以上で、 *expression1*が*expression2*以下である場合にのみ、ステートメントが TRUE を返すようにすることができます。
