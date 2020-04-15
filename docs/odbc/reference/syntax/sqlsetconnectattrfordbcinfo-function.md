---
title: 関数を接続します。マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectAttrForDbcInfo function [ODBC]
ms.assetid: a28fadb9-b998-472a-b252-709507e92005
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9f43a0fc6cd02fe566579a543667f9a4c4c1a108
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301889"
---
# <a name="sqlsetconnectattrfordbcinfo-function"></a>SQLSetConnectAttrForDbcInfo 関数
**適合 性**  
 バージョン導入: ODBC 3.81 標準準拠: ODBC  
  
 **まとめ**  
 **SQLSetConnectAttrForDbcInfo**は**SQLSetConnectAttr**と同じですが、接続ハンドルではなく接続情報トークンに属性を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp
  
SQLRETURN  SQLSetConnectAttrForDbcInfo(  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                SQLINTEGER            Attribute,  
                SQLPOINTER            ValuePtr,  
                SQLINTEGER            StringLength );  
```  
  
## <a name="arguments"></a>引数  
 *トークン*  
 [入力]トークン ハンドル。  
  
 *属性*  
 [入力]設定する属性。 有効な属性の一覧は、ドライバ固有のもので[、SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)の場合と同じです。  
  
 *ValuePtr*  
 [入力]*属性*に関連付ける値へのポインター。 *属性*の値に応じて*ValuePtr*は 32 ビット符号なし整数値になるか、NULL で終わる文字列を指します。 *Attribute*引数がドライバ固有の値である場合 *、ValuePtr*の値は符号付き整数である可能性があることに注意してください。  
  
 *文字列の長さ*  
 [入力]*属性*が ODBC で定義された属性で *、ValuePtr*が文字列またはバイナリ バッファを指している場合、この引数は **ValuePtr*の長さになります。 文字列データの場合、この引数には文字列のバイト数を含める必要があります。  
  
 *属性*が ODBC で定義された属性で *、ValuePtr*が整数の場合、*文字列長*は無視されます。  
  
 *属性*がドライバー定義の属性である場合、アプリケーションは*StringLength*引数を設定してドライバー マネージャーに属性の性質を示します。 *文字列長*には、次の値を指定できます。  
  
-   *ValuePtr*が文字列へのポインタである場合、*文字列*または文字列の長さSQL_NTS。  
  
-   *ValuePtr*がバイナリ バッファへのポインタである場合、アプリケーションは SQL_LEN_BINARY_ATTR(*長さ*) マクロの結果を*StringLength*に格納します。 この場合は、負の値が*文字列長に*設定されます。  
  
-   *ValuePtr*が文字列またはバイナリ文字列以外の値へのポインターである場合 *、StringLength*には値がSQL_IS_POINTER。  
  
-   *ValuePtr*に固定長の値が含まれている場合 *、StringLength*はSQL_IS_INTEGERまたはSQL_IS_UINTEGERのいずれかです。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)と同じですが、ドライバー マネージャーは、SQL_HANDLE_DBC_INFO_TOKENの**ハンドル型**と*hDbcInfoToken*の**ハンドル**を使用します。  
  
## <a name="remarks"></a>解説  
 **SQLSetConnectAttrForDbcInfo**は**SQLSetConnectAttr**と同じですが、接続ハンドルではなく接続情報トークンに属性を設定します。 たとえば **、SQLSetConnectAttr**が属性を認識しない**場合、その**属性のSQL_ERRORも返す必要があります。  
  
 ドライバーがSQL_ERRORまたはSQL_INVALID_HANDLEを返すたびに、ドライバーはプール ID を計算するには、この属性を無視する必要があります。 また、ドライバー マネージャーは *、hDbcInfoToken*から診断情報を取得し[、sqlConnect と SQLDriverConnect](../../../odbc/reference/syntax/sqlconnect-function.md)でアプリケーションにSQL_SUCCESS_WITH_INFOを返[します](../../../odbc/reference/syntax/sqldriverconnect-function.md)。 したがって、アプリケーションは、一部の属性を設定できない理由の詳細を取得できます。  
  
 アプリケーションはこの関数を直接呼び出さないでください。 ドライバー対応接続プールをサポートする ODBC ドライバーは、この関数を実装する必要があります。  
  
 ODBC ドライバ開発用に sqlspi.h を含めます。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [ODBC ドライバー対応接続プールの開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
