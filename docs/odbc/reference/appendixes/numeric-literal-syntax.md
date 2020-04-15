---
title: 数値リテラル構文 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC literals [ODBC], numeric
- numeric literals [ODBC]
- literals [ODBC], numeric
ms.assetid: fb17498d-4f1d-4b3d-b33d-1e62c7d3c32d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e035e3ec53c5b5494c029d6840b9f5c836821209
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299862"
---
# <a name="numeric-literal-syntax"></a>数値リテラルの構文
ODBC の数値リテラルには、次の構文が使用されます。  
  
 *数値リテラル*::=*符号付き数値リテラル&#124;符号なし数値リテラル*  
  
 *符号付き数値リテラル*::= [*符号*]*符号なし数値リテラル*  
  
 *符号なし数値リテラル*::=*正確な数値リテラル&#124;近似数値リテラル*  
  
 *正確な数値リテラル*::=*符号なし整数*[*ピリオド*[*符号なし整数*]&#124;*符号なし整数*  
  
 *符号*::=*プラス記号&#124;マイナス記号*  
  
 *概数リテラル*::=*仮数 E 指数*  
  
 *カマティッサ*::=*正確な数値リテラル*  
  
 *指数*::=*符号付き整数*  
  
 *符号付き整数*::= [*符号*]*符号なし整数*  
  
 *符号なし整数*::=*桁.*  
  
 *プラス記号*::=*+*  
  
 *マイナス記号*::= -  
  
 *digit* :=1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; &#124; &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *期間*::= .
