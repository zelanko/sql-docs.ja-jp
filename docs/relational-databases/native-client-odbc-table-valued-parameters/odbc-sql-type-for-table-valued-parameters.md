---
title: テーブル値パラメーターの ODBC SQL 型 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL_SS_TABLE
ms.assetid: 6725bfb9-5f10-4115-be09-fd9c9f5779ea
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6aae522544f4d9532dbc2d71db1b3d55ebee3da5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297842"
---
# <a name="odbc-sql-type-for-table-valued-parameters"></a>テーブル値パラメーター用の ODBC SQL 型
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  テーブル値パラメーターは、新しい ODBC SQL 型である SQL_SS_TABLE でサポートされます。  
  
## <a name="remarks"></a>解説  
 SQL_SS_TABLE は、他の ODBC データ型または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型に変換できません。  
  
 SQL_SS_TABLEが SQLBindParameter の*ValueType*パラメーターで C データ型として使用される場合、またはアプリケーション・パラメーター記述子 (APD) レコードのSQL_DESC_TYPEを SQL_SS_TABLE に設定しようとした場合、SQL_ERRORが戻され、SQLSTATE=HY003「無効なアプリケーション・バッファー・タイプ」で診断レコードが生成されます。  
  
 IPD レコードで SQL_DESC_TYPE を SQL_SS_TABLE に設定し、対応するアプリケーション パラメーター記述子レコードが SQL_C_DEFAULT ではない場合、SQL_ERROR が返され、"アプリケーションのバッファー型が無効です" というメッセージで SQLSTATE=HY003 の診断レコードが生成されます。 これは、SQL セットデスフィールド、SQL セットデスクレル、または SQLBind パラメーターの*パラメーターの型*で発生する可能性があります。  
  
 SQLGetData を呼び出すときに*TargetType*パラメーターがSQL_SS_TABLE場合、SQL_ERRORが返され、SQLSTATE=HY003「無効なアプリケーション・バッファー・タイプ」を使用して診断レコードが生成されます。  
  
 テーブル値パラメーターの列は、SQL_SS_TABLE 型としてバインドできません。 *パラメーター・タイプ*を SQL_SS_TABLE に設定して**SQLBindParameter**が呼び出されると、SQL_ERRORが戻され、SQLSTATE=HY004「無効な SQL データ・タイプ」を使用して診断レコードが生成されます。 これは、SQL セットデスフィールドと SQL セットデスクレを使用しても発生する可能性があります。  
  
 テーブル値パラメーターの列の値には、パラメーターおよび結果列と同じデータ変換オプションが設定されています。  
  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降では、テーブル値パラメーターは入力パラメーターのみに使用できます。 SQLBindParameter または SQLSetDescField を使用してSQL_DESC_PARAMETER_TYPEをSQL_PARAM_INPUT以外の値に設定しようとすると、SQL_ERRORが返され、SQLSTATE=HY105 とメッセージ "無効なパラメーターの型" のステートメントに診断レコードが追加されます。  
  
 テーブル値パラメーターの列は *、 StrLen_or_IndPtr*でSQL_DEFAULT_PARAMを使用できません。 代わりに、アプリケーションで列の属性 SQL_CA_SS_COL_HAS_DEFAULT_VALUE を 1 に設定できます。 つまり、この列にすべての行の既定値が含まれます。 *StrLen_or_IndPtrが*SQL_DEFAULT_PARAMに設定されている場合、SQLExecute または SQLExecDirect はSQL_ERRORを返し、SQLSTATE=HY090 とメッセージ "無効な文字列またはバッファー長" を持つステートメントに診断レコードが追加されます。  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;テーブル値パラメーター](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
