---
title: テーブル値パラメーター用の ODBC SQL 型 |マイクロソフトのドキュメント
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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9eb67883cd580aecee8b4e41eae67c3e2dfc4856
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68129212"
---
# <a name="odbc-sql-type-for-table-valued-parameters"></a>テーブル値パラメーター用の ODBC SQL 型
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  テーブル値パラメーターは、新しい ODBC SQL 型である SQL_SS_TABLE でサポートされます。  
  
## <a name="remarks"></a>コメント  
 SQL_SS_TABLE は、他の ODBC データ型または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型に変換できません。  
  
 SQL_SS_TABLE が C のデータ型として使用されるかどうか、 *ValueType* SQL_DESC_TYPE を SQL_SS_TABLE にアプリケーション パラメーター記述子 (APD) レコードで設定するされる SQLBindParameter、または試行のパラメーターと、SQL_ERROR が返されると、診断レコードが生成されます SQLSTATE = HY003、「無効なアプリケーション バッファーの種類」。  
  
 IPD レコードで SQL_DESC_TYPE を SQL_SS_TABLE に設定し、対応するアプリケーション パラメーター記述子レコードが SQL_C_DEFAULT ではない場合、SQL_ERROR が返され、"アプリケーションのバッファー型が無効です" というメッセージで SQLSTATE=HY003 の診断レコードが生成されます。 これに該当、 *ParameterType* SQLSetDescField、SQLSetDescRec SQLBindParameter の。  
  
 場合、 *TargetType* SQLGetData を呼び出すときに、パラメーターが SQL_SS_TABLE、SQL_ERROR が返され、sqlstate 診断レコードが生成された = HY003、「無効なアプリケーション バッファーの種類」です。  
  
 テーブル値パラメーターの列は、SQL_SS_TABLE 型としてバインドできません。 場合**SQLBindParameter**を使用して呼び出した*ParameterType*を SQL_SS_TABLE に設定すると、SQL_ERROR が返され、sqlstate 診断レコードが生成された = HY004、「無効な SQL データ型」です。 SQLSetDescField および SQLSetDescRec これにも該当します。  
  
 テーブル値パラメーターの列の値には、パラメーターおよび結果列と同じデータ変換オプションが設定されています。  
  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降では、テーブル値パラメーターは入力パラメーターのみに使用できます。 = HY105 とメッセージ"無効なパラメーターの SQL_DESC_PARAMETER_TYPE を SQLBindParameter または SQLSetDescField SQL_PARAM_INPUT 以外の値に設定しようとしましたが、SQL_ERROR が返され、診断レコードが sqlstate ステートメントに追加する場合"を入力します。  
  
 テーブル値パラメーター列に SQL_DEFAULT_PARAM を使用できない*StrLen_or_IndPtr*テーブル値パラメーターの行ごとの既定値はサポートされていません。 代わりに、アプリケーションで列の属性 SQL_CA_SS_COL_HAS_DEFAULT_VALUE を 1 に設定できます。 つまり、この列にすべての行の既定値が含まれます。 場合*StrLen_or_IndPtr*設定を SQL_DEFAULT_PARAM SQLExecute、SQLExecDirect または SQL_ERROR を返し、診断レコードは、sqlstate ステートメントに追加されます = HY090 と"無効な文字列長またはバッファー長"のメッセージ。  
  
## <a name="see-also"></a>関連項目  
 [テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
