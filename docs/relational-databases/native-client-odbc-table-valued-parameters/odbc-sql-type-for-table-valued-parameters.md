---
title: テーブル値パラメーター用の ODBC SQL 型 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL_SS_TABLE
ms.assetid: 6725bfb9-5f10-4115-be09-fd9c9f5779ea
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 87436164f2a1177bc19ca80f2bfa53079120aa63
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="odbc-sql-type-for-table-valued-parameters"></a>テーブル値パラメーター用の ODBC SQL 型
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  テーブル値パラメーターは、新しい ODBC SQL 型である SQL_SS_TABLE でサポートされます。  
  
## <a name="remarks"></a>解説  
 SQL_SS_TABLE は、他の ODBC データ型または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型に変換できません。  
  
 SQL_SS_TABLE はから C データ型として使用されているかどうか、 *ValueType* SQLBindParameter、またはしようとしてのパラメーターが SQL_SS_TABLE にアプリケーション パラメーター記述子 (APD) レコードで SQL_DESC_TYPE を設定しようとして、SQL_ERROR が返されると、sqlstate の診断レコードが生成 = HY003、「無効なアプリケーション バッファー型」です。  
  
 IPD レコードで SQL_DESC_TYPE を SQL_SS_TABLE に設定し、対応するアプリケーション パラメーター記述子レコードが SQL_C_DEFAULT ではない場合、SQL_ERROR が返され、"アプリケーションのバッファー型が無効です" というメッセージで SQLSTATE=HY003 の診断レコードが生成されます。 これに該当、 *ParameterType* SQLSetDescField、SQLSetDescRec SQLBindParameter のです。  
  
 場合、 *TargetType*パラメーターが SQL_SS_TABLE の SQLGetData を呼び出すときに、SQL_ERROR が返され、診断レコードが生成 sqlstate = HY003、「無効なアプリケーション バッファー型」です。  
  
 テーブル値パラメーターの列は、SQL_SS_TABLE 型としてバインドできません。 場合**SQLBindParameter**で呼び出された*ParameterType* SQL_SS_TABLE に設定すると、SQL_ERROR が返され、sqlstate の診断レコードが生成 HY004、「無効な SQL データ型」を = です。 Sqlsetdescfield によると SQLSetDescRec これも発生します。  
  
 テーブル値パラメーターの列の値には、パラメーターおよび結果列と同じデータ変換オプションが設定されています。  
  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降では、テーブル値パラメーターは入力パラメーターのみに使用できます。 SQLBindParameter または SQLSetDescField SQL_PARAM_INPUT 以外の値に SQL_DESC_PARAMETER_TYPE を設定しようとしましたが、SQL_ERROR が返され、診断レコードが sqlstate ステートメントに追加されると = HY105 およびメッセージ"無効なパラメーター"を入力します。  
  
 テーブル値パラメーターの列に SQL_DEFAULT_PARAM を使用できない*StrLen_or_IndPtr*行ごとの既定値はテーブル値パラメーターではサポートされていないため、します。 代わりに、アプリケーションで列の属性 SQL_CA_SS_COL_HAS_DEFAULT_VALUE を 1 に設定できます。 つまり、この列にすべての行の既定値が含まれます。 場合*StrLen_or_IndPtr*設定を SQL_DEFAULT_PARAM SQLExecute または SQLExecDirect は SQL_ERROR を返し、診断レコードは sqlstate ステートメントに追加する = HY090 およびメッセージ「無効な文字列長またはバッファー長」です。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
