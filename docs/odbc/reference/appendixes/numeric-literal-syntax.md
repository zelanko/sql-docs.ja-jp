---
title: 数値リテラルの構文 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9daa81e2e0c2e927ee7407d4a00d5d48c333bd54
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67990723"
---
# <a name="numeric-literal-syntax"></a>数値リテラルの構文
ODBC の数値リテラルには、次の構文が使用されます。  
  
 *数値リテラル*:: =*符号付き数値リテラル &#124; 符号なし数値リテラル*  
  
 *符号付き数値リテラル*:: = [*sign*]*符号なし数値リテラル*  
  
 *符号なし-* 数値リテラル:: =*真数リテラル &#124; 概数-リテラル*  
  
 *真数リテラル*:: = *unsigned-integer* [*period*[*符号なし*整数]] *&#124;ピリオド符号なし整数*  
  
 *sign* :: =*プラス記号 &#124; マイナス記号*  
  
 *概数-リテラル*:: =*仮数 E 指数*  
  
 *仮数*:: =*完全な数値リテラル*  
  
 *指数*:: =*符号付き整数*  
  
 *符号付き整数*:: = [*sign*]*符号なし整数*  
  
 *符号なし整数*:: = *digit...*  
  
 *プラス記号*:: =*+*  
  
 *負符号*:: =-  
  
 *digit* :: = 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *期間*:: =。
