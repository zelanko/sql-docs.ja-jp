---
title: "SQLSTATE マッピング |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compatibility [ODBC], SQLSTATE
- backward compatibility [ODBC], SQLSTATE
- SQLSTATE [ODBC]
ms.assetid: 6e6cabcf-a204-40eb-b77d-8a0c4a5e8524
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: da687563cfa1b2031c6537294bbaedcbb67f7a02
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlstate-mappings"></a>SQLSTATE マッピング
このトピックでは、ODBC 2 の SQLSTATE 値について説明します。*x*および ODBC 3 *。x*です。 ODBC 3 の詳細についてはします。*x* SQLSTATE 値を参照してください[付録 a: ODBC エラー コード](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md)です。  
  
 ODBC 3 です。*x*S1xxx ではなく HYxxx SQLSTATEs が返されます、および S00XX ではなく 42Sxx SQLSTATEs が返されます。 これは、Open Group および ISO 標準に合うように行われました。 多くの場合、標準がいくつかの SQLSTATEs の解釈を再定義があるため、マッピングは一対一ありません。  
  
 ODBC 2 時にします。*x*アプリケーションは、ODBC 3 にアップグレードします*。x* ODBC 3 の期待に変更するアプリケーションでは、アプリケーションが*。x* ODBC 2 ではなく SQLSTATEs *。x* SQLSTATEs です。 次の表には、ODBC 3 が一覧表示します。*x* SQLSTATEs される各 ODBC 2 *。x* SQLSTATE にマップします。  
  
 また環境属性が SQL_OV_ODBC2 に設定されている場合、ドライバーは ODBC 2 をポストします。*x* ODBC 3 ではなく SQLSTATEs *。x* SQLSTATEs とき**SQLGetDiagField**または**SQLGetDiagRec**と呼びます。 特定のマッピングは、ODBC 2 注目することで決定できます*.x* ODBC 3 に対応する次の表の 1 列目の SQLSTATE *。x*列 2 の SQLSTATE。  
  
|ODBC 2 です。*x* SQLSTATE|ODBC 3 です。*x* SQLSTATE|コメント|  
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
|S1002|07009|ODBC 2 です。*x* SQLSTATE S1002 は ODBC 3 にマップします*。x* SQLSTATE 07009 場合は、基になる関数**SQLBindCol**、 **SQLColAttribute**、 **SQLExtendedFetch**、 **SQLFetch**、 **SQLFetchScroll**、または**SQLGetData**です。|  
|S1003|HY003||  
|S1004|HY004||  
|S1008|HY008||  
|S1009|HY009|Null ポインターの無効な使用に返されます。|  
|S1009|HY024|無効な属性値に対して返されます。|  
|S1009|HY092|更新データの削除の呼び出しによって返される**SQLSetPos**、または追加、更新、またはへの呼び出しによってデータを削除する**SQLBulkOperations**同時実行性が読み取り専用の場合、します。|  
|S1010|HY007 HY010|SQLSTATE S1010 が SQLSTATE HY007 にマップされているときに**SQLDescribeCol**呼び出しの前に呼び出されます**SQLPrepare**、 **SQLExecDirect**、または、のカタログ関数*StatementHandle*です。 それ以外の場合、SQLSTATE S1010 SQLSTATE HY010 がマップされます。|  
|S1011|HY011||  
|S1012|HY012||  
|S1090|HY090||  
|S1091|HY091||  
|S1092|HY092||  
|S1093|07009|ODBC 3 です。*x* 07009 SQLSTATE は ODBC 2 にマップします*。x*基になる終了した場合は、SQLSTATE S1093 **SQLBindParameter**または**SQLDescribeParam**です。|  
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
|S1C00|HYC00||  
|S1T00|HYT00||  
  
> [!NOTE]  
>  ODBC 3 です。*x* 07008 SQLSTATE は ODBC 2 にマップします*。x* SQLSTATE S1000 です。

