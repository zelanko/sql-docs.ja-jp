---
title: 環境、接続、およびステートメントの属性 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- environment attributes [ODBC]
- connection attributes [ODBC]
- statement attributes [ODBC]
ms.assetid: 9e15b276-3b7a-428a-b72f-a3ddfe1ba1ce
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4606b4345cc52d1371649449890400e01dbc5f51
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114352"
---
# <a name="environment-connection-and-statement-attributes"></a>環境、接続、およびステートメント属性
ODBC では、環境、接続、またはステートメントに関連付けられている多数の属性が定義されています。  
  
 環境属性は、接続プールが有効になっているかどうかなど、環境全体に影響を与えます。 環境属性は**SQLSetEnvAttr**で設定され、 **SQLGetEnvAttr**を使用して取得されます。  
  
 接続属性は、データソースへの接続を試行している間にドライバーが待機する時間など、各接続に個別に影響を与えます。接続属性は**SQLSetConnectAttr**で設定され、 **Sqlgetconnectattr**を使用して取得されます。 接続属性の詳細については、「[接続属性](../../../odbc/reference/develop-app/connection-attributes.md)」を参照してください。  
  
 ステートメント属性は、ステートメントを非同期的に実行する必要があるかどうかなど、各ステートメントに個別に影響します。 ステートメント属性は、 **SQLSetStmtAttr**で設定され、 **SQLGetStmtAttr**を使用して取得されます。 いくつかのステートメント属性は読み取り専用の属性であり、設定することはできません。 たとえば、カーソルの現在の行の数を取得するために使用される SQL_ATTR_ROW_NUMBER statement 属性は読み取り専用です。 ステートメント属性の詳細については、「[ステートメント属性](../../../odbc/reference/develop-app/statement-attributes.md)」を参照してください。  
  
 ODBC で定義されている属性に加えて、ドライバーは独自の接続とステートメントの属性を定義できます。 ドライバーで定義された属性を Open Group に登録して、2つのドライバーベンダーが独自の異なる属性に同じ整数値を割り当てないようにする必要があります。 詳細については、「[ドライバー固有のデータ型、記述子の型、情報の種類、診断の種類、および属性](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md)」を参照してください。  
  
 属性の完全な一覧については、「 [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)、 [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)、および[SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)」を参照してください。 ほとんどの属性は、それらが影響する ODBC 関数の説明にも記述されています。
