---
title: SQLBindParameter |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLBindParameter function
ms.assetid: c302c87a-e7f4-4d2b-a0a7-de42210174ac
caps.latest.revision: 46
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: d4d310df4126e34324ef0e16be0952f5b53c748f
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2018
ms.locfileid: "35699113"
---
# <a name="sqlbindparameter"></a>SQLBindParameter
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLBindParameter**のデータを提供するために使用されるときに、データ変換の負荷を排除することができます、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー、アプリケーションのクライアントとサーバーの両方のコンポーネントのパフォーマンスが大幅にします。 その他に、概数データ型を挿入または更新するときに有効桁数を失うことが少なくなるという利点もあります。  
  
> [!NOTE]  
>  挿入するときに**char**と**wchar**バイナリ形式に変換後のデータのサイズではなく、型のデータを image 列に渡されるデータのサイズを使用します。  
  
 パラメーター配列の配列要素の 1 つで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバー エラーが発生しても、残りの配列要素に対しては引き続きステートメントが実行されます。 アプリケーションがこのステートメントのパラメーター状態要素の配列をバインドした場合は、その配列を基にして、エラーが発生したパラメーター行を特定できます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーを使用する場合は、入力パラメーターのバインド時に SQL_PARAM_INPUT を指定します。 OUTPUT キーワードで定義されたストアド プロシージャ パラメーターをバインドするときは、SQL_PARAM_OUTPUT または SQL_PARAM_INPUT_OUTPUT のみを指定してください。  
  
 [SQLRowCount](../../relational-databases/native-client-odbc-api/sqlrowcount.md)は信頼できません、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーの場合は、バインドされたパラメーター配列の配列要素とステートメントの実行でエラーが発生します。 また、ODBC ステートメント属性 SQL_ATTR_PARAMS_PROCESSED_PTR は、エラーが発生する前に処理された行数を報告します。 その後、必要に応じてパラメーター状態配列全体をアプリケーションで調査することにより、正常に実行されたステートメント数を検出できます。  
  
## <a name="binding-parameters-for-sql-character-types"></a>SQL 文字型のパラメーターのバインド  
 渡された SQL データ型が型の場合、文字、 *ColumnSize*文字 (バイトではなく) でのサイズします。 バイト単位でデータ文字列の長さが 8000 より大きい場合*ColumnSize*に設定する必要があります**SQL_SS_LENGTH_UNLIMITED**SQL 型のサイズに制限がないことを示すです。  
  
 インスタンスの場合は、SQL データ型は**SQL_WVARCHAR**、 *ColumnSize* 4000 を超えることができないする必要があります。 かどうか、実際のデータ長が 4000 より長い、し*ColumnSize*に設定する必要があります**SQL_SS_LENGTH_UNLIMITED**ように**nvarchar (max)** ドライバーによって使用されます。  
  
## <a name="sqlbindparameter-and-table-valued-parameters"></a>SQLBindParameter とテーブル値パラメーター  
 他のパラメーター型と同様に、テーブル値パラメーターは、SQLBindParameter によってバインドされます。  
  
 テーブル値パラメーターがバインドされた後、そのパラメーターの列もバインドされます。 列をバインドするを呼び出す[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) SQL_SOPT_SS_PARAM_FOCUS にテーブル値パラメーターの序数を設定します。 次に、テーブル値パラメーターの各列に対して SQLBindParameter を呼び出します。 最上位パラメーター バインドに戻るには、SQL_SOPT_SS_PARAM_FOCUS に 0 を設定します。  
  
 テーブル値パラメーターの記述子フィールドへのマッピングのパラメーターについては、次を参照してください。[バインドおよび Data Transfer of Table-Valued パラメーターと列の値](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)です。  
  
 テーブル値パラメーターの詳細については、次を参照してください。[テーブル値パラメーター &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)です。  
  
## <a name="sqlbindparameter-support-for-enhanced-date-and-time-features"></a>SQLBindParameter による機能強化された日付と時刻のサポート  
 」の説明に従って、日付/時刻型のパラメーターの値は変換は[C から SQL への変換](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)です。 注型のパラメーター**時間**と**datetimeoffset**必要があります*ValueType*として指定された**SQL_C_DEFAULT**または**SQL_C_BINARY**場合は、対応する構造体 (**SQL_SS_TIME2_STRUCT**と**SQL_SS_TIMESTAMPOFFSET_STRUCT**) を使用します。  
  
 詳細については、次を参照してください。[日付と時刻の強化&#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)です。  
  
## <a name="sqlbindparameter-support-for-large-clr-udts"></a>SQLBindParameter による大きな CLR UDT のサポート  
 **SQLBindParameter**大きなの CLR ユーザー定義型 (Udt) をサポートしています。 詳細については、次を参照してください。 [Large CLR User-Defined 型&#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)です。  
  
## <a name="see-also"></a>参照  
 [ODBC API 実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SQLBindParameter 関数](http://go.microsoft.com/fwlink/?LinkId=59328)  
  
  
