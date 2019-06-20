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
manager: craigg
ms.openlocfilehash: 18b1c144e84bf0be5aaeb68b66660f7bc7865ade
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181279"
---
# <a name="numeric-literal-syntax"></a>数値リテラルの構文
次の構文は、ODBC での数値リテラルに使用されます。  
  
 *数値リテラル*:: =*符号付き数値リテラル&#124;符号なし数値リテラル*  
  
 *signed-numeric-literal* ::= [*sign*] *unsigned-numeric-literal*  
  
 *符号なし数値リテラル*:: =*正確な数値リテラル&#124;おおよその数値リテラル*  
  
 *exact-numeric-literal* ::= *unsigned-integer* [*period*[*unsigned-integer*]] *&#124;period unsigned-integer*  
  
 *サインオン*:: =*プラス記号&#124;マイナス記号*  
  
 *おおよその数値リテラル*:: =*仮数 E の指数*  
  
 *仮数*:: =*正確な数値リテラル*  
  
 *指数*:: =*符号付き整数*  
  
 *signed-integer* ::= [*sign*] *unsigned-integer*  
  
 *符号なし整数*:: =*桁.*  
  
 *プラス記号*:: = *+*  
  
 *マイナス記号*:: = -  
  
 *数字*:: = 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 &#124; 0  
  
 *期間*:: =。
