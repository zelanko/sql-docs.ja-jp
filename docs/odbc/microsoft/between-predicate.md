---
title: 述語の間 |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283859"
---
# <a name="between-predicate"></a>BETWEEN 述語
構文は次のとおりです。  
  
```  
expression1 BETWEEN expression2 AND expression3  
```  
  
 *式 1*が式 2 以上、式*1*が*式* *3*以下の場合にのみ true を返します。  
  
 この構文のセマンティクスは、デスクトップ データベース ドライバと Microsoft Jet エンジンで異なります。 Microsoft Jet SQL では、*式 2*を式 3 より大きく設定すると、式 1 が式*3*以上、*式 1*が*式* *2*以上の場合にのみ*TRUE*が返されます。
