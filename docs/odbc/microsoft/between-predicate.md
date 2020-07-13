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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1f3ff800938574bec81e9cbb86839e014085a2a8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81283859"
---
# <a name="between-predicate"></a>BETWEEN 述語
構文は次のとおりです。  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 *expression1*が*expression2*以上で*expression1*が*expression3*以下である場合にのみ true を返します。  
  
 この構文のセマンティクスは、デスクトップデータベースドライバーと Microsoft Jet エンジンによって異なります。 Microsoft Jet SQL では、 *expression2*は*expression3*よりも大きくすることができます。 *expression1*が*expression3*以上で、 *expression1*が*expression2*以下である場合にのみ、ステートメントが TRUE を返すようにすることができます。
