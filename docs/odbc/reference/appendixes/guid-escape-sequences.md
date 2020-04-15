---
title: GUID エスケープ シーケンス |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC escape sequences [ODBC], GUID
- escape sequences [ODBC], guid
- guid escape sequence [ODBC]
ms.assetid: 71d43ef9-4a31-493e-b9e0-f864e9ef3ce6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 44907bfbd884bf361ce5f2ab8b3f6d8a247aba44
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306973"
---
# <a name="guid-escape-sequences"></a>GUID エスケープ シーケンス
ODBC は、GUID リテラルにエスケープ シーケンスを使用します。 このエスケープシーケンスの構文は次のとおりです。  
  
```  
{guid 'nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn'}  
```  
  
## <a name="remarks"></a>解説  
 BNF 表記では、構文は次のとおりです。  
  
 *ODBC GUID エスケープ*::=  
     *ODBC-esc-イニシエーターの GUID*'*GUID 値*' ODBC *esc-終端文字*  
  
 *ODBC-esc-イニシエーター* ::= {  
  
 *ODBC-esc 終止符*::= }  
  
 *guid-value* ::=*クロック低値の GUID 区切り記号クロック -ミドル値の GUID 区切り記号クロック -高値の GUID 区切り記号クロック-セパレーター ノード値*  
  
 *GUID 区切り記号*::= -  
  
 *クロック低値*::= hex_digit *hex_digithex_digithex_digithex_digithex_digit hex_digit hex_digithex_digithex_digit*  
  
 *クロック中間値*::= *hex_digithex_digithex_digithex_digit*  
  
 *クロック高値*::= *hex_digithex_digithex_digithex_digit*  
  
 *クロック・セク値*::= *hex_digithex_digithex_digit hex_digithex_digit*  
  
 *クロックノード値*::hex_digit hex_digit hex_digit hex_digit hex_digit *hex_digit hex_digit=* hex_digithex_digitのhex_digithex_digitをhex_digithex_digithex_digithex_digithex_digithex_digitをhex_digithex_digithex_digit  
  
 *hex_digit* ::= 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 9 &#124; A &#124; B &#124; &#124; C &#124; D &#124; D &#124; E &#124; F &#124; 7  
  
 GUID リテラルエスケープ シーケンスは、GUID データ型がデータ ソースでサポートされている場合にサポートされます。 アプリケーションは、このデータ型がサポートされているかどうかを判断するのに**は SQLGetTypeInfo**を呼び出す必要があります。
