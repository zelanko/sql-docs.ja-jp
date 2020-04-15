---
title: 環境、接続、およびステートメントの属性 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 86cecaf0b82c7b6d15b3f37262507d2cff0c3c10
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300932"
---
# <a name="environment-connection-and-statement-attributes"></a>環境、接続、およびステートメント属性
ODBC は、環境、接続、またはステートメントに関連付けられた属性を多数定義します。  
  
 環境属性は、接続プールが有効かどうかなど、環境全体に影響します。 環境属性は **、SQLSetEnvAttr**で設定され **、SQLGetEnvAttr**で取得されます。  
  
 接続属性は、タイムアウト前にデータ ソースに接続する際にドライバーが待機する時間など、各接続に個別に影響します。接続属性は**SQLSetConnectAttr**で設定され **、SQLGetConnectAttr**で取得されます。 接続属性の詳細については、「[接続](../../../odbc/reference/develop-app/connection-attributes.md)属性」を参照してください。  
  
 ステートメント属性は、ステートメントを非同期で実行するかどうかなど、各ステートメントに個別に影響します。 ステートメント属性は **、SQLSetStmtAttr**で設定され **、SQLGetStmtAttr**で取得されます。 いくつかのステートメント属性は読み取り専用属性であり、設定できません。 たとえば、カーソルの現在の行の番号を取得するために使用されるSQL_ATTR_ROW_NUMBERステートメント属性は読み取り専用です。 ステートメント属性の詳細については、「ステートメント属性[」を](../../../odbc/reference/develop-app/statement-attributes.md)参照してください。  
  
 ODBC によって定義される属性に加えて、ドライバーは独自の接続属性とステートメント属性を定義できます。 2 つのドライバー ベンダーが異なる独自の属性に同じ整数値を割り当てないように、ドライバー定義の属性を Open Group に登録する必要があります。 詳細については、「[ドライバ固有のデータ型、記述子の型、情報の種類、診断の種類、および属性](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md)」を参照してください。  
  
 属性の完全な一覧については[、「SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md) [、SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)」、および[「SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)」を参照してください。 ほとんどの属性は、影響を与える ODBC 関数の説明にも記述されています。
