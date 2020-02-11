---
title: 文字列関数 (Visual FoxPro ODBC ドライバー) |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: db1fbaffbee0f74625f4a11cad3b961f194e3829
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67948776"
---
# <a name="string-functions-visual-foxpro-odbc-driver"></a>文字列関数 (Visual FoxPro ODBC ドライバー)
次の表に、Visual FoxPro ODBC ドライバーでサポートされている ODBC 文字列操作関数の一覧を示します。同じ関数の Visual FoxPro 文法が ODBC 構文と異なる場合は、Visual FoxPro と同等のものが表示されます。  
  
|ODBC 文法|Visual FoxPro の文法|  
|------------------|---------------------------|  
|ASCII *(string_exp)*|ASC *(string_exp)*|  
|CHAR *(コード)*|CHR *(string_exp)*|  
|CONCAT *(string_exp1、string_exp2)*|*string_exp1 + string_exp2*|  
|相違点 *(string_exp1、string_exp2)*||  
|INSERT *(string_exp1、start、length、string_exp2)*|*(String_exp1、開始、長さ、string_exp2)*|  
|LCASE *(string_exp)*|LOWER *(string_exp)*|  
|LEFT *(string_exp, count)*||  
|長さ *(string_exp)*|LEN *(string_exp)*|  
|LTRIM *(string_exp)*||  
|REPEAT *(string_exp, count)*|REPLICATE *(string_exp, count)*|  
|REPLACE *(string_exp1、string_exp2、string_exp3)*|STRTRAN *(string_exp1、string_exp2、string_exp3)*|  
|RIGHT *(string_exp、count)*||  
|RTRIM *(string_exp)*||  
|SOUNDEX *(string_exp)*||  
|領域 *(カウント)*||  
|SUBSTRING *(string_exp、start、length)*|SUBSTR *(string_exp、start、length)*|  
|UCASE *(string_exp)*|UPPER *(string_exp)*|
