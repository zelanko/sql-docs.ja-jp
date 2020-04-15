---
title: プロシージャ コール |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], procedure calls
- procedure calls [ODBC]
ms.assetid: 145130cc-40e7-4722-8417-dff131084752
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a9c52e72512c8b81c6872461207f235ea2731ac5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282232"
---
# <a name="procedure-calls"></a>プロシージャ呼び出し
*プロシージャ*は、データ ソースに格納されている実行可能オブジェクトです。 これは通常、プリコンパイルされた 1 つ以上の SQL ステートメントです。 プロシージャを呼び出すエスケープ シーケンスは、  
  
 **{****,**[**?**]**呼び出し***プロシージャ名*[*parameter***] [***パラメータ*]**)**]**}**  
  
 プロシージャ*名 はプロシージャ*の名前を指定し、*パラメータ*はプロシージャ パラメータを指定します。  
  
 プロシージャ コールエスケープ シーケンスの詳細については、「付録 C: SQL 文法」の[「プロシージャコールエスケープシーケンス](../../../odbc/reference/appendixes/procedure-call-escape-sequence.md)」を参照してください。  
  
 プロシージャには、0 個以上のパラメーターを指定できます。 また、構文の先頭にオプションのパラメーター マーカー **?=** で示されているように、値を返すこともできます。 *パラメーター*が入力パラメーターまたは入出力パラメーターの場合、リテラルまたはパラメーター・マーカーを指定できます。 ただし、一部のデータ ソースではリテラル パラメーター値を受け入れないため、相互運用可能なアプリケーションでは常にパラメーター マーカーを使用する必要があります。 *パラメーター*が出力パラメーターの場合は、パラメーター・マーカーでなければなりません。 プロシージャー呼び出しステートメントを実行する前に、パラメーター・マーカーを**SQLBindParameter**でバインドする必要があります。  
  
 プロシージャ呼び出しでは、入力パラメーターと入出力パラメーターを省略できます。 プロシージャがかっこ付きで呼び出されるが、パラメーターがない場合 ({call *procedure-name*()}) は、ドライバーは最初のパラメーターの既定値を使用するようにデータ ソースに指示します。 プロシージャにパラメーターがない場合は、プロシージャが失敗する可能性があります。 プロシージャがかっこなしで呼び出された場合 ({call *procedure-name*} など)、ドライバーはパラメーター値を送信しません。  
  
 プロシージャ呼び出しでは、入力パラメーターや入出力パラメーターとしてリテラルを指定できます。 たとえば **、InsertOrder**プロシージャに 5 つの入力パラメーターがあるとします。 次の**InsertOrder**の呼び出しでは、最初のパラメーターを省略し、2 番目のパラメーターのリテラルを提供し、3 番目、4 番目、および 5 番目のパラメーターのパラメーター マーカーを使用します。  
  
```  
{call InsertOrder(, 10, ?, ?, ?)}   // Not interoperable!  
```  
  
 パラメーターを省略した場合は、他のパラメーターから区切るコンマを使用する必要があります。 入力パラメーターまたは入出力パラメーターを省略すると、プロシージャはそのパラメーターの既定値を使用します。 入力パラメータまたは入出力パラメータのデフォルト値を指定するもう1つの方法は、パラメータにバインドされた長さ/インジケーターバッファの値をSQL_DEFAULT_PARAMに設定することです。  
  
 入出力パラメーターが省略された場合、またはパラメーターにリテラルが指定されている場合、ドライバーは出力値を破棄します。 同様に、プロシージャの戻り値のパラメーター マーカーを省略した場合、ドライバーは戻り値を破棄します。 最後に、値を返さないプロシージャに戻り値パラメーターを指定すると、ドライバーは、そのパラメーターにバインドされる長さ/インジケーター バッファーの値を SQL_NULL_DATA に設定します。  
  
 プロシージャPARTS_IN_ORDERS特定の部品番号を含む注文のリストを含む結果セットを作成するとします。 次のコードは、部品番号 544 のこのプロシージャを呼び出します。  
  
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
  
 データ ソースがプロシージャをサポートしているかどうかを確認するために、アプリケーションは SQL_PROCEDURES オプションを指定して**SQLGetInfo**を呼び出します。  
  
 手順の詳細については、「[手順](../../../odbc/reference/develop-app/procedures-odbc.md)」を参照してください。
