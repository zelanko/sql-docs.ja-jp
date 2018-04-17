---
title: プロシージャ呼び出し |Microsoft ドキュメント
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
ms.topic: article
helpviewer_keywords:
- escape sequences [ODBC], procedure calls
- procedure calls [ODBC]
ms.assetid: 145130cc-40e7-4722-8417-dff131084752
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b12586b2da965ef159766e670ecc9456260c75d3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="procedure-calls"></a>プロシージャ呼び出し
A*プロシージャ*データ ソースに格納されている実行可能オブジェクトです。 これは通常、プリコンパイルされた 1 つ以上の SQL ステートメントです。 プロシージャを呼び出すためのエスケープ シーケンスは、します。  
  
 **{****[? =]****呼び出す***プロシージャ名*[**(**[*パラメーター*] [**、**[*パラメーター*].**)**]**}**  
  
 ここで*プロシージャ名*プロシージャの名前を指定し、*パラメーター*プロシージャのパラメーターを指定します。  
  
 プロシージャ呼び出しのエスケープ シーケンスの詳細については、次を参照してください。[プロシージャ Call エスケープ シーケンス](../../../odbc/reference/appendixes/procedure-call-escape-sequence.md)付録 c: SQL の文法でします。  
  
 プロシージャには、0 個以上のパラメーターを指定できます。 省略可能なパラメーター マーカーに従い、値を返すことも**? =**構文の先頭にします。 場合*パラメーター*が入力パラメーターまたは入出力パラメーターでは、リテラルまたはパラメーター マーカーを指定できます。 ただし、一部のデータ ソースはリテラル パラメーター値を受理しないために、相互運用可能アプリケーションはパラメーター マーカーを使用常にする必要があります。 場合*パラメーター*出力パラメーター、パラメーター マーカーをする必要があります。 パラメーター マーカーにバインドする必要があります**SQLBindParameter**プロシージャ呼び出しの前にステートメントを実行します。  
  
 プロシージャ呼び出しでは、入力パラメーターと入出力パラメーターを省略できます。 かどうか、プロシージャが呼び出さかっこでは、パラメーターを使用せずなど {呼び出す*プロシージャ名*()}、ドライバーは、最初のパラメーターの既定値を使用するデータ ソースを指示します。 プロシージャは、パラメーターを持たない場合の処理が失敗する可能性がします。 プロシージャがかっこがない場合などと呼ばれるかどうかは {呼び出す*プロシージャ名*}、ドライバーは、パラメーターの値を送信しません。  
  
 プロシージャ呼び出しでは、入力パラメーターや入出力パラメーターとしてリテラルを指定できます。 たとえば、プロシージャ**InsertOrder**に 5 つの入力パラメーターです。 次の呼び出しに**InsertOrder**最初のパラメーターを省略して、2 番目のパラメーターのリテラルを提供および第 3、4 番目、および 5 番目のパラメーター マーカーを使用してパラメーター。  
  
```  
{call InsertOrder(, 10, ?, ?, ?)}   // Not interoperable!  
```  
  
 パラメーターを省略すると、その他のパラメーターを区切るコンマ必要がありますも表示されることに注意してください。 入力パラメーターまたは入出力パラメーターを省略すると、プロシージャはそのパラメーターの既定値を使用します。 長さ/インジケーター バッファーの値を設定するパラメーターまたは入出力パラメーターの既定値を指定する別の方法は、SQL_DEFAULT_PARAM をパラメーターにバインドします。  
  
 入力/出力パラメーターを省略した場合、またはパラメーターのリテラルを指定する場合は、ドライバーは出力値を破棄します。 同様に、プロシージャの戻り値のパラメーター マーカーを省略した場合、ドライバーは戻り値を破棄します。 最後に、値を返さないプロシージャに戻り値パラメーターを指定すると、ドライバーは、そのパラメーターにバインドされる長さ/インジケーター バッファーの値を SQL_NULL_DATA に設定します。  
  
 たとえば、PARTS_IN_ORDERS プロシージャは、特定の部分の数を含む注文の一覧を含む結果セットを作成します。 次のコードは、部品番号 544 にこのプロシージャを呼び出します。  
  
```  
SQLUINTEGER   PartID;  
SQLINTEGER    PartIDInd = 0;  
  
// Bind the parameter.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_SLONG, SQL_INTEGER, 0, 0,  
                  &PartID, 0, PartIDInd);  
  
// Place the department number in PartID.  
PartID = 544;  
  
// Execute the statement.  
SQLExecDirect(hstmt, "{call PARTS_IN_ORDERS(?)}", SQL_NTS);  
```  
  
 データ ソースがプロシージャをサポートしているかどうかを決定するには、アプリケーションを呼び出す**SQLGetInfo** SQL_PROCEDURES オプションを使用します。  
  
 プロシージャの詳細については、次を参照してください。[プロシージャ](../../../odbc/reference/develop-app/procedures-odbc.md)です。
