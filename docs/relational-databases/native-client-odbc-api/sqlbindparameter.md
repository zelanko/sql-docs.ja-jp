---
title: 場合は、SQLBindParameter |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLBindParameter function
ms.assetid: c302c87a-e7f4-4d2b-a0a7-de42210174ac
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 67fb8dafdabb4a9a9df60c4592f206c9106224ab
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68115249"
---
# <a name="sqlbindparameter"></a>SQLBindParameter
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **場合は、SQLBindParameter**のデータを提供するために使用するときに、データ変換の負担をなくすことができます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアントの ODBC ドライバー、アプリケーションのクライアントとサーバーの両方のコンポーネントに大幅なパフォーマンス向上の結果です。 その他に、概数データ型を挿入または更新するときに有効桁数を失うことが少なくなるという利点もあります。  
  
> [!NOTE]  
>  挿入時に**文字**と**wchar**バイナリ形式に変換後のデータのサイズとは対照的に渡されるデータのサイズ、イメージ列の種類のデータを使用します。  
  
 パラメーター配列の配列要素の 1 つで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー エラーが発生しても、残りの配列要素に対しては引き続きステートメントが実行されます。 アプリケーションがこのステートメントのパラメーター状態要素の配列をバインドした場合は、その配列を基にして、エラーが発生したパラメーター行を特定できます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーを使用する場合は、入力パラメーターのバインド時に SQL_PARAM_INPUT を指定します。 OUTPUT キーワードで定義されたストアド プロシージャ パラメーターをバインドするときは、SQL_PARAM_OUTPUT または SQL_PARAM_INPUT_OUTPUT のみを指定してください。  
  
 [では](../../relational-databases/native-client-odbc-api/sqlrowcount.md)の信頼性が低い、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアントの ODBC ドライバーの場合は、バインドされたパラメーター配列の配列要素、ステートメントの実行でエラーが発生します。 また、ODBC ステートメント属性 SQL_ATTR_PARAMS_PROCESSED_PTR は、エラーが発生する前に処理された行数を報告します。 その後、必要に応じてパラメーター状態配列全体をアプリケーションで調査することにより、正常に実行されたステートメント数を検出できます。  
  
## <a name="binding-parameters-for-sql-character-types"></a>SQL 文字型のパラメーターのバインド  
 渡される SQL データ型が、文字型の場合*ColumnSize*文字 (バイトではなく) のサイズです。 (バイト単位)、データの文字列の長さが 8000 より大きい場合*ColumnSize*に設定する必要があります**SQL_SS_LENGTH_UNLIMITED**SQL 型のサイズに制限がないことを示します。  
  
 たとえば、SQL データ型の場合**SQL_WVARCHAR**、 *ColumnSize* 4000 より大きくする必要がありますできません。 実際のデータ長がより大きいかどうか、4000、 *ColumnSize*に設定する必要があります**SQL_SS_LENGTH_UNLIMITED**ように**nvarchar (max)** ドライバーによって使用されます。  
  
## <a name="sqlbindparameter-and-table-valued-parameters"></a>SQLBindParameter とテーブル値パラメーター  
 テーブル値パラメーターは、他のパラメーターの型のような場合は、SQLBindParameter がバインドされます。  
  
 テーブル値パラメーターがバインドされた後、そのパラメーターの列もバインドされます。 列をバインドするを呼び出す[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) SQL_SOPT_SS_PARAM_FOCUS にテーブル値パラメーターの序数を設定します。 テーブル値パラメーターの列ごとに、場合は、SQLBindParameter を呼び出してください。 最上位パラメーター バインドに戻るには、SQL_SOPT_SS_PARAM_FOCUS に 0 を設定します。  
  
 テーブル値パラメーターの記述子フィールドへのマッピングのパラメーターに関する情報を参照してください[バインドおよび Data Transfer of Table-Valued パラメーターと列の値](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)です。  
  
 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)します。  
  
## <a name="sqlbindparameter-support-for-enhanced-date-and-time-features"></a>SQLBindParameter による機能強化された日付と時刻のサポート  
 日付/時刻型のパラメーターの値で説明したように変換[C から SQL への変換](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)。 注型のパラメーター**時間**と**datetimeoffset**必要があります*ValueType*として指定された**SQL_C_DEFAULT**または**SQL_C_BINARY**場合、対応する構造体 (**SQL_SS_TIME2_STRUCT**と**SQL_SS_TIMESTAMPOFFSET_STRUCT**) 使用されます。  
  
 詳細については、次を参照してください。[日付と時刻の強化&#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)します。  
  
## <a name="sqlbindparameter-support-for-large-clr-udts"></a>SQLBindParameter による大きな CLR UDT のサポート  
 **場合は、SQLBindParameter**大きい CLR ユーザー定義型 (Udt) がサポートされています。 詳細については、次を参照してください。 [Large CLR User-Defined 型&#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)します。  
  
## <a name="see-also"></a>参照  
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SQLBindParameter 関数](https://go.microsoft.com/fwlink/?LinkId=59328)  
  
  
