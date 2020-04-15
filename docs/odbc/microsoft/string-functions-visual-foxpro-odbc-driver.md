---
title: 文字列関数 (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC string functions [ODBC]
- string functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], string functions
- FoxPro ODBC driver [ODBC], string functions
ms.assetid: 1974fd26-ef0d-45d5-860b-298917c8e9c3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 988ba23b95f6b138148b1fa17ad303d7aa2dc895
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299192"
---
# <a name="string-functions-visual-foxpro-odbc-driver"></a>文字列関数 (Visual FoxPro ODBC ドライバー)
次の表は、Visual FoxPro ODBC ドライバーでサポートされている ODBC 文字列操作関数の一覧です。同じ関数の Visual FoxPro 文法が ODBC 構文と異なる場合は、対応するビジュアル FoxPro が一覧表示されます。  
  
|ODBC 文法|ビジュアルフォックスプロ文法|  
|------------------|---------------------------|  
|ASCII *(string_exp)*|ASC *(string_exp)*|  
|文字 *(コード)*|CHR *(string_exp)*|  
|コンキャット *(string_exp1、string_exp2)*|*string_exp1 + string_exp2*|  
|違い *(string_exp1、string_exp2)*||  
|INSERT *(string_exp1、開始、長さ、string_exp2)*|*STUFF(string_exp1、スタート、長さ、string_exp2)*|  
|LCASE *(string_exp)*|下*段 (string_exp)*|  
|左 *(string_exp、カウント)*||  
|長さ *(string_exp)*|レン *(string_exp)*|  
|LTRIM *(string_exp)*||  
|繰り返し *(string_exp、カウント)*|レプリケート *(string_exp、カウント)*|  
|置換 *(string_exp1、string_exp2、string_exp3)*|ストラン *(string_exp1、string_exp2、string_exp3)*|  
|右 *(string_exp、カウント)*||  
|RTRIM *(string_exp)*||  
|サネックス *(string_exp)*||  
|スペース *(カウント)*||  
|サブストリング *(string_exp、開始、長さ)*|SUBSTR *(string_exp、開始、長さ)*|  
|ウケーstring_exp *(string_exp)*|アッパー *(string_exp)*|
