---
title: ディスプレイサイズ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- display size of data types [ODBC]
- size of data types [ODBC]
- data types [ODBC], display size
- SQL data types [ODBC], column characteristics
ms.assetid: 9f7f766f-2492-463c-aab7-f2476e222042
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 578bf0cbdf2dd1dbd06dd4a248f4efa5eb839916
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307033"
---
# <a name="display-size"></a>表示サイズ
列の表示サイズは、文字形式でデータを表示するために必要な最大文字数です。 次の表は、各 ODBC SQL データ型の表示サイズを定義しています。  
  
|SQL タイプ識別子|ディスプレイ サイズ|  
|-------------------------|------------------|  
|すべての文字タイプ[a]|データを文字形式で表示するために必要な文字の数 (固定型の場合) または最大 (変数型の場合) の文字数。|  
|SQL_DECIMAL SQL_NUMERIC|列の精度に 2 を加えた値 (符号、*精度*の桁数、および小数点)。 例えば、NUMERIC(10,3) として定義された列の表示サイズは 12 です。|  
|SQL_BIT|1 (1 桁)。|  
|SQL_TINYINT|符号付きの場合は 4 (符号と 3 桁) または符号なし (3 桁) の場合は 3。|  
|SQL_SMALLINT|符号付きの場合は 6 (符号と 5 桁) または符号なし (5 桁) の場合は 5。|  
|SQL_INTEGER|符号付きの場合は 11 (符号と 10 桁) または符号なし (10 桁) の場合は 10。|  
|SQL_BIGINT|20 (符号と 19 桁の符号、符号なしの場合は 20 桁)。|  
|SQL_REAL|14 (符号、7 桁、小数点、文字*E、* 符号、および 2 桁)。|  
|SQL_FLOATSQL_DOUBLE|24 (符号、15 桁、小数点、文字*E、* 符号、および 3 桁)。|  
|すべてのバイナリ型[a]|列の 2 倍の定義された長さ(変数型の場合)の長さ。 (各 2 進バイトは 2 桁の 16 進数で表されます。|  
|SQL_TYPE_DATE|10 *(yyyy-mm-dd*形式の日付)。|  
|SQL_TYPE_TIME|8 (時刻形式*hh:mm:ss)*<br /><br /> - または -<br /><br /> 9 + *s* *(hh:mm:ss*[.fff.]の形式の時刻で *、s*は秒の小数部の精度です)。|  
|SQL_TYPE_TIMESTAMP|19 *(yyyy-mm-dd hh:mm:ss*形式のタイムスタンプの場合)<br /><br /> - または -<br /><br /> 20 + *s* *(yyyy-mm-dd hh:mm:ss*[.fff.]] 形式のタイムスタンプの場合 *、s*は秒の小数部の精度です)。|  
|すべての間隔データ型|[「間隔データ型の長さ](../../../odbc/reference/appendixes/interval-data-type-length.md)」を参照してください。|  
|SQL_GUID|36 *(aaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeee*の文字数|  
  
 [a] ドライバーが列または変数の型のパラメーターの長さを決定できない場合、SQL_NO_TOTAL返します。
