---
title: "GUID のエスケープ シーケンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC escape sequences [ODBC], GUID
- escape sequences [ODBC], guid
- guid escape sequence [ODBC]
ms.assetid: 71d43ef9-4a31-493e-b9e0-f864e9ef3ce6
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d4ed6e517d9a8fa6f4c28c7b05541d36262df2a8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="guid-escape-sequences"></a>GUID のエスケープ シーケンス
ODBC では、GUID のリテラルのエスケープ シーケンスを使用します。 このエスケープ シーケンスの構文は次のとおりです。  
  
```  
{guid 'nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn'}  
```  
  
## <a name="remarks"></a>解説  
 BNF 表記で、構文のとおりです。  
  
 *ODBC guid エスケープ*:: =  
     *ODBC esc イニシエーター guid* '*guid 値*' *esc 終端の ODBC*  
  
 *ODBC esc イニシエーター* :: = {  
  
 *Esc 終端の ODBC* :: =}  
  
 *guid 値*:: =*時計と低値 guid の区切りクロック中間値 guid の区切りクロック高価値の guid の区切りクロック seq 値 guid の区切りノード値*  
  
 *guid の区切り*:: = -  
  
 *クロックの価値の低い*:: = *hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *クロック中間値*:: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *クロックの価値の高い*:: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *クロック seq 値*:: = *hex_digit hex_digit hex_digit hex_digit*  
  
 *クロック ノード値*:: = *hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit hex_digit*  
  
 *hex_digit* :: 0 (&) #124; 1 &#124; = 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9 & #124 です。A & #124 です。B & #124 です。C & #124 です。D & #124 です。E & #124 です。F  
  
 GUID データ型が、データ ソースによってサポートされている場合、GUID のリテラルのエスケープ シーケンスはサポートされています。 アプリケーションを呼び出す必要があります**SQLGetTypeInfo**をこのデータ型はサポートされているかどうかを判断します。

