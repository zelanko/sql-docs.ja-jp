---
title: 文字列関数 (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC string functions [ODBC]
- string functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], string functions
- FoxPro ODBC driver [ODBC], string functions
ms.assetid: 1974fd26-ef0d-45d5-860b-298917c8e9c3
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a5f201eee732fa316873919deaabc4d07610a015
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="string-functions-visual-foxpro-odbc-driver"></a>文字列関数 (Visual FoxPro ODBC ドライバー)
次の表に、Visual FoxPro ODBC ドライバーでサポートされている ODBC 文字列操作関数同じ関数の場合、Visual FoxPro 文法は、ODBC 構文によって異なります、同等の Visual FoxPro が一覧表示されます。  
  
|ODBC の文法|Visual FoxPro 文法|  
|------------------|---------------------------|  
|ASCII *(string_exp)*|ASC *(string_exp)*|  
|CHAR *(コード)*|CHR *(string_exp)*|  
|CONCAT *(string_exp1、string_exp2)*|*string_exp1 + string_exp2*|  
|違い *(string_exp1、string_exp2)*||  
|挿入 *(string_exp1、開始、長さ、string_exp2)*|STUFF *(string_exp1、開始、長さ、string_exp2)*|  
|LCASE *(string_exp)*|低い *(string_exp)*|  
|左 *(string_exp、数)*||  
|長さ *(string_exp)*|LEN *(string_exp)*|  
|LTRIM *(string_exp)*||  
|繰り返し *(string_exp、数)*|レプリケート *(string_exp、数)*|  
|置き換える *(string_exp1、string_exp2、string_exp3)*|STRTRAN *(string_exp1、string_exp2、string_exp3)*|  
|右 *(string_exp、数)*||  
|RTRIM *(string_exp)*||  
|SOUNDEX *(string_exp)*||  
|領域 *(数)*||  
|部分文字列 *(string_exp、開始、長さ)*|SUBSTR *(string_exp、開始、長さ)*|  
|UCASE *(string_exp)*|上限 *(string_exp)*|
