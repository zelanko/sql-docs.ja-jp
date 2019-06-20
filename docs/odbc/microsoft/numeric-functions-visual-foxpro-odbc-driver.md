---
title: 数値関数 (Visual FoxPro ODBC ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC numeric functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], numeric functions
- numeric functions [ODBC]
- FoxPro ODBC driver [ODBC], numeric functions
ms.assetid: 7caab48e-cbb5-4bbc-a09b-5cf902e5bc45
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73379b769da61fe14ba18815446337d0172c2805
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63045486"
---
# <a name="numeric-functions-visual-foxpro-odbc-driver"></a>数値関数 (Visual FoxPro ODBC ドライバー)
次の表に、Visual FoxPro ODBC ドライバーでサポートされている ODBC 数値関数ODBC 構文から同じ関数の場合、Visual FoxPro の文法が異なる場合は、Visual FoxPro のと同じですが一覧表示されます。  
  
|ODBC の文法|Visual FoxPro の文法|  
|------------------|---------------------------|  
|ABS *(numeric_exp)*||  
|ACOS *(float_exp)*||  
|ASIN *(float_exp)*||  
|ATAN *(float_exp)*||  
|ATAN2 *(float_exp1 float_exp2)*|ATN2 (*float_exp1、float_exp2*)|  
|CEILING *(numeric_exp)*||  
|COS *(float_exp)*||  
|COT *(float_exp)*||  
|DEGREES *(numeric_exp)*|RTOD *(numeric_exp)*|  
|EXP *(float_exp)*||  
|FLOOR *(numeric_exp)*||  
|ログ *(float_exp)*||  
|LOG10 *(float_exp)*||  
|MOD *(integer_exp1 integer_exp2)*||  
|PI *( )*||  
|RADIANS *(numeric_exp)*|DTOR *(numeric_exp)*|  
|RAND *([integer_exp])*||  
|ROUND *(numeric_exp integer_exp)*||  
|SIGN *(numeric_exp)*||  
|SIN *(float_exp)*||  
|SQRT *(float_exp)*||  
|TAN *(float_exp)*||  
  
 次の数値関数はサポートされていません。  
  
 POWER *(numeric_exp, integer_exp)*  
  
 TRUNCATE *(numeric_exp integer_exp)*
