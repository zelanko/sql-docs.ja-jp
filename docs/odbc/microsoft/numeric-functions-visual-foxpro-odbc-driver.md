---
title: 数値関数 (ビジュアル フォックスプロ ODBC ドライバ) |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d3993a9a1b2412cb15229f2763c7c3b38f6b7862
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298162"
---
# <a name="numeric-functions-visual-foxpro-odbc-driver"></a>数値関数 (Visual FoxPro ODBC ドライバー)
次の表は、ビジュアル フォックスプロ ODBC ドライバーでサポートされている ODBC 数値関数を示しています。同じ関数の Visual FoxPro 文法が ODBC 構文と異なる場合は、対応するビジュアル FoxPro が一覧表示されます。  
  
|ODBC 文法|ビジュアルフォックスプロ文法|  
|------------------|---------------------------|  
|ABS *(numeric_exp)*||  
|アコス *(float_exp)*||  
|アシン *(float_exp)*||  
|アタン *(float_exp)*||  
|ATAN2 *(float_exp1、 float_exp2)*|ATN2 (*float_exp1, float_exp2*)|  
|天井 *(numeric_exp)*||  
|コス *(float_exp)*||  
|COT *(float_exp)*||  
|度 *(numeric_exp)*|RTOD *(numeric_exp)*|  
|EXP *(float_exp)*||  
|フロア *(numeric_exp)*||  
|ログ *(float_exp)*||  
|ログ10 *(float_exp)*||  
|MOD *(integer_exp1、integer_exp2)*||  
|PI *( )*||  
|ラジアン *(numeric_exp)*|DTOR *(numeric_exp)*|  
|ランド *([integer_exp])*||  
|ラウンド *(numeric_exp、integer_exp)*||  
|記号 *(numeric_exp)*||  
|罪 *(float_exp)*||  
|SQRT *(float_exp)*||  
|タン *(float_exp)*||  
  
 次の数値関数はサポートされていません。  
  
 パワー *(numeric_exp、integer_exp)*  
  
 切り捨て *(numeric_exp、integer_exp)*
