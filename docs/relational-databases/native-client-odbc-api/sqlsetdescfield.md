---
title: Sqlsetdescfield による |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-api
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQLSetDescField function
ms.assetid: de4bed15-15be-4825-994c-1046255e725a
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8f1953e5f8f7f4b7326600ec24c8e688040d4deb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32943187"
---
# <a name="sqlsetdescfield"></a>SQLSetDescField
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Sqlsetdescfield によるは、テーブル値パラメーターおよびテーブル値パラメーター列の記述子フィールドの設定を使用できます。 使用可能なフィールドの詳細については、次を参照してください。[テーブル値パラメーターの記述子フィールド](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameter-descriptor-fields.md)と[テーブル値パラメーターの構成要素の列の記述子フィールド](../../relational-databases/native-client-odbc-table-valued-parameters/descriptor-fields-for-table-valued-parameter-constituent-columns.md)です。  
  
## <a name="remarks"></a>解説  
 テーブル値パラメーター列は、記述子のヘッダー フィールド SQL_SOPT_SS_PARAM_FOCUS に、SQL_DESC_TYPE が SQL_SS_TABLE に設定されているレコードの序数が設定される場合のみ使用できます。 SQL_SOPT_SS_PARAM_FOCUS の詳細については、次を参照してください。 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)です。  
  
 場合、テーブル値パラメーターではないパラメーターの序数に SQL_SOPT_SS_PARAM_FOCUS を設定しようとしましたが、SQLSetStmtAttr SQL_ERROR を返し、診断レコードが作成 sqlstate = HY024 メッセージ「無効な属性値」です。 SQL_SOPT_SS_PARAM_FOCUS は、SQL_ERROR が返されたときに変更されません。  
  
 SQL_SOPT_SS_PARAM_FOCUS に 0 を設定すると、パラメーターの記述子レコードへのアクセスが復元されます。  
  
 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター (&) #40";"ODBC"&"#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)です。  
  
## <a name="sqlsetdescfield-support-for-enhanced-date-and-time-features"></a>SQLSetDescField による機能強化された日付と時刻のサポート  
 ODBC では、日付と時刻の機能が強化されました。 新しい日付/時刻型に指定された記述子フィールドについては、次を参照してください。[パラメーターと結果のメタデータ](../../relational-databases/native-client-odbc-date-time/metadata-parameter-and-result.md)です。  
  
 詳細については、次を参照してください。[日付と時刻の強化 (&) #40";"ODBC"&"#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)です。  
  
## <a name="sqlsetdescfield-support-for-large-clr-udts"></a>SQLSetDescField による大きな CLR UDT のサポート  
 Sqlsetdescfield による大きなの CLR ユーザー定義型 (Udt) をサポートしています。 詳細については、次を参照してください。 [Large CLR User-Defined 型 (&) #40";"ODBC"&"#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)です。  
  
## <a name="sqlsetdescfield-support-for-sparse-columns"></a>SQLSetDescField によるスパース列のサポート  
 SQLSetDecField 値 SQL_SS_NAME_SCOPE_EXTENDED および SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET にアプリケーション パラメーター記述子 (APD) の SQL_SOPT_SS_NAME_SCOPE の設定を使用できます。  
  
 詳細については、次を参照してください。[スパース列のサポート&#40;ODBC&#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [Sqlsetdescfield による](http://go.microsoft.com/fwlink/?LinkId=80705)   
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
