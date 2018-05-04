---
title: SQLSetConnectAttrForDbcInfo 関数 |Microsoft ドキュメント
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
- SQLSetConnectAttrForDbcInfo function [ODBC]
ms.assetid: a28fadb9-b998-472a-b252-709507e92005
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 990c0074d7408d3b200bbff1ba1d43a46e77fd1e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetconnectattrfordbcinfo-function"></a>SQLSetConnectAttrForDbcInfo 関数
**準拠**  
 のバージョンで導入されました ODBC 3.81 規格に準拠: ODBC。  
  
 **概要**  
 **SQLSetConnectAttrForDbcInfo**と同じ**SQLSetConnectAttr**が、接続ハンドルでの代わりに、接続情報トークンで属性を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
SQLRETURN  SQLSetConnectAttrForDbcInfo(  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                SQLINTEGER            Attribute,  
                SQLPOINTER            ValuePtr,  
                SQLINTEGER            StringLength );  
```  
  
## <a name="arguments"></a>引数  
 *hDbcInfoToken*  
 [入力]トークンのハンドル。  
  
 *属性*  
 [入力]設定する属性です。 有効な属性の一覧は、特定のドライバーと同じである[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)です。  
  
 *ValuePtr*  
 [入力]関連付けられる値へのポインター*属性*です。 値に応じて*属性*、 *ValuePtr* 32 ビット符号なし整数の値であるかが null で終わる文字列を指します。 されている場合、*属性*引数は、ドライバー固有の値の値*ValuePtr*符号付き整数である可能性があります。  
  
 *stringLength*  
 [入力]場合*属性*ODBC で定義された属性と*ValuePtr*文字の文字列またはバイナリ バッファーへのポインター、この引数の長さにする必要があります **ValuePtr*です。 文字の文字列データでは、この引数は、文字列のバイト数を含める必要があります。  
  
 場合*属性*ODBC で定義された属性と*ValuePtr*整数*StringLength*は無視されます。  
  
 場合*属性*ドライバーの定義済みの属性は、アプリケーション、ドライバー マネージャーに属性の性質を示す設定、 *StringLength*引数。 *StringLength*次の値を持つことができます。  
  
-   場合*ValuePtr*文字の文字列へのポインターが*StringLength* SQL_NTS または文字列の長さです。  
  
-   場合*ValuePtr*アプリケーションが、SQL_LEN_BINARY_ATTR の結果を配置し、バイナリのバッファーへのポインターは、(*長さ*) マクロで*StringLength*です。 これにより、配置に負の値*StringLength*です。  
  
-   場合*ValuePtr*文字の文字列またはバイナリ文字列以外の値へのポインターが*StringLength* SQL_IS_POINTER 値でなければなりません。  
  
-   場合*ValuePtr*し、固定長の値を含む*StringLength*は SQL_IS_INTEGER か SQL_IS_UINTEGER、必要に応じて。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 同じ[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)、ドライバー マネージャーを使用する点を除いて、 **HandleType** SQL_HANDLE_DBC_INFO_TOKEN のおよび**処理**の*hDbcInfoToken*.  
  
## <a name="remarks"></a>解説  
 **SQLSetConnectAttrForDbcInfo**と同じ**SQLSetConnectAttr**が、接続ハンドルでの代わりに、接続情報トークンの属性を設定します。 たとえば場合、 **SQLSetConnectAttr**属性では認識されません**SQLSetConnectAttrForDbcInfo**その属性の SQL_ERROR を返しますもする必要があります。  
  
 ドライバーには、SQL_ERROR または SQL_INVALID_HANDLE が返されます、されるたびに、ドライバーはプール ID を計算するには、この属性を無視します。 また、ドライバー マネージャーは、診断情報を取得から*hDbcInfoToken*でのアプリケーションに SQL_SUCCESS_WITH_INFO を返すと[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)と[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md). そのため、アプリケーションでは、いくつかの属性を設定できない理由に関する詳細を取得できます。  
  
 アプリケーションでは、この関数を直接呼び出さないでください。 ドライバー対応接続プールをサポートする ODBC ドライバーでは、この関数を実装する必要があります。  
  
 ODBC ドライバーの開発の sqlspi.h が含まれます。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [ODBC ドライバー対応接続プールの開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
