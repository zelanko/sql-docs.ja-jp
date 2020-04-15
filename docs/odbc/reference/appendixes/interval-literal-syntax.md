---
title: 間隔リテラル構文 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- literals [ODBC], interval
- interval literals [ODBC]
- ODBC literals [ODBC], interval
ms.assetid: 2f2d22c1-51d6-4055-9f5a-53bc31e9fea0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3387b07a8e769206a6a495addff4287000691fec
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290572"
---
# <a name="interval-literal-syntax"></a>Interval のリテラルの構文
ODBC の間隔リテラルには、次の構文が使用されます。  
  
 *間隔リテラル ::= INTERVAL* [+*&#124;*- 間隔*ストリング間隔修飾子*  
  
 *間隔文字列*::=*引用符*{*年-月リテラル*&#124;*日-リテラル*}*引用*  
  
 *年-月リテラル*::=*年値*&#124; [*年-* 値 -]*月値*  
  
 *日時間リテラル*::=*曜日-時間間隔*&#124;*時間間隔*  
  
 *日中の時間間隔*::=*日値*[*時間値*]:*分値*[:*秒値*]]  
  
 *時間間隔*::=*時間値*[:*分値*[:*秒値*] ]  
  
 &#124;*分値*[:*秒値*]  
  
 &#124;*秒値*  
  
 *年-値*::=*日時値*  
  
 *月値*::=*日時値*  
  
 *日値*::=*日時値*  
  
 *時間値*::=*日時値*  
  
 *分値*::=*日時値*  
  
 *秒値*::=*秒整数値*[.]*秒分数*]]  
  
 *秒整数値*::=*符号なし整数*  
  
 *秒分数*::=*符号なし整数*  
  
 *日付時刻値*::=*符号なし整数*  
  
 *間隔修飾子*::=*開始フィールド*TO*終了フィールド*&#124;*単一日付時刻フィールド*  
  
 *開始フィールド*::=*非秒日付時刻フィールド*[(*間隔先行フィールド精度*)]  
  
 *終了フィールド*::=*秒以外の日時フィールド*&#124; SECOND[(*間隔分数秒精度*)]  
  
 *単一日付時刻フィールド*::=*非秒日付時刻フィールド*[(間隔*先行フィールド精度*)] &#124; SECOND[(*間隔先行フィールド精度*[,*間隔分数秒精度*)]  
  
 *日付時刻フィールド*::=*非秒の日時フィールド*&#124; SECOND  
  
 *非秒日付時刻フィールド*::= 年 &#124; 月 &#124; 日 &#124; 時間 &#124; 分  
  
 *間隔小数分秒精度*::=*符号なし整数*  
  
 *間隔先行フィールド精度*::=*符号なし整数*  
  
 *引用*::= '  
  
 *符号なし整数*::=*桁.*
