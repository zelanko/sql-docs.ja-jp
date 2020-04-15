---
title: マッピング |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLSTATE
- backward compatibility [ODBC], SQLSTATE
- SQLSTATE [ODBC]
ms.assetid: 6e6cabcf-a204-40eb-b77d-8a0c4a5e8524
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec58c0e41869529bbba5fd31ad534976923a990d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299742"
---
# <a name="sqlstate-mappings"></a>SQLSTATE マッピング
このトピックでは、ODBC *2.x*および ODBC *3.x*の SQLSTATE 値について説明します。 ODBC *3.x* SQLSTATE 値の詳細については、「[付録 A: ODBC エラー コード](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md)」を参照してください。  
  
 ODBC *3.x*では、S1xxx の代わりに HYxxx SQLSTATE が返され、S00XX の代わりに 42Sxx SQLSTATE が返されます。 これは、オープングループとISO規格に合わせて行われました。 多くの場合、標準がいくつかの SQLSTATE の解釈を再定義しているため、マッピングは 1 対 1 ではありません。  
  
 ODBC *2.x*アプリケーションを ODBC *3.x*アプリケーションにアップグレードする場合、ODBC *2.x* SQLSTATE ではなく ODBC *3.x* SQLSTATE を期待するようにアプリケーションを変更する必要があります。 次の表は、各 ODBC *2.x* SQLSTATE がマップされる ODBC *3.x* SQLSTATE を示しています。  
  
 SQL_ATTR_ODBC_VERSION環境属性がSQL_OV_ODBC2に**SQLGetDiagRec**設定されている場合、ドライバーは **、ODBC** 3.x SQLSTATE ではなく ODBC *2.x* SQLSTATE をポストします。 *3.x* 次の表の 1 桁目にある ODBC *2.x* SQLSTATE に、2 列目の ODBC 3.x SQLSTATE に対応する ODBC *2.x* SQLSTATE に注意して、特定のマッピングを決定できます。  
  
|ODBC *2.x* SQLSTATE|ODBC *3.x* SQLSTATE|説明|  
|-------------------------|-------------------------|--------------|  
|01S03|01001||  
|01S04|01001||  
|22003|HY019||  
|22008|22007||  
|22005|22018||  
|24000|07005||  
|37000|42000||  
|70100|HY018||  
|S0001|42S01||  
|S0002|42S02||  
|S0011|42S11||  
|S0012|42S12||  
|S0021|42S21||  
|S0022|42S22||  
|S0023|42S23||  
|S1000|HY000||  
|S1001|HY001||  
|S1002|07009|ODBC *2.x* SQLSTATE S1002 は、基になる関数が**SQL バインドコル****、SQLCol 属性**、SQLExtendedFetch、SQLFetch、SQLFetchScroll、**SQLFetch**または**SQLGetData**である場合、ODBC *3.x* SQLSTATE 07009 にマップされます。 **SQLExtendedFetch** **SQLFetchScroll**|  
|S1003|HY003||  
|S1004|HY004||  
|S1008|HY008||  
|S1009|HY009|null ポインターの無効な使用に対して返されます。|  
|S1009|HY024|無効な属性値に対して返されます。|  
|S1009|HY092|**SQLSetPos**の呼び出しによってデータを更新または削除する場合、または**SQLBulkOperations**の呼び出しによってデータを追加、更新、または削除するために、同時実行が読み取り専用である場合に返されます。|  
|S1010|HY007 HY010|SQLSTATE S1010 は、SQLPrepare **、SQLExecDirect、** または*ステートメント ハンドル*のカタログ関数を呼び出す前に**SQLDescribeCol**が呼び出されたときに**SQLSTATE**HY007 にマップされます。 それ以外の場合は、SQLSTATE S1010 が SQLSTATE HY010 にマップされます。|  
|S1011|HY011||  
|S1012|HY012||  
|S1090|HY090||  
|S1091|HY091||  
|S1092|HY092||  
|S1093|07009|ODBC *3.x* SQLSTATE 07009 は、基になる関数が**SQLBind パラメータ**または**SQLDescribe パラム**である場合、ODBC *2.x* SQLSTATE S1093 にマップされます。|  
|S1096|HY096||  
|S1097|HY097||  
|S1098|HY098||  
|S1099|HY099||  
|S1100|HY100||  
|S1101|HY101||  
|S1103|HY103||  
|S1104|HY104||  
|S1105|HY105||  
|S1106|HY106||  
|S1107|HY107||  
|S1108|HY108||  
|S1109|HY109||  
|S1110|HY110||  
|S1111|HY111||  
|S1C00|ハイク00||  
|S1T00|ヒュット00||  
  
> [!NOTE]  
>  ODBC *3.x* SQLSTATE 07008 は、ODBC *2.x* SQLSTATE S1000 にマップされます。
