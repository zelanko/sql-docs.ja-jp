---
title: SQL 属性 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLColAttribute function
ms.assetid: a5387d9e-a243-4cfe-b786-7fad5842b1d6
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6113316f3be68ca03b5c107ed54965577b6963c8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302631"
---
# <a name="sqlcolattribute"></a>SQLColAttribute
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **SQLColAttribute**を使用して、準備済みまたは実行される ODBC ステートメントの結果セット列の属性を取得できます。 準備済みステートメントで**SQLColAttribute**を呼[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]び出すと、 へのラウンドトリップが発生します。 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ODBC ドライバーは、ステートメントの実行の一部として結果セットの列データを受け取るので **、SQLExecute**または**SQLExecDirect**の完了後に**SQLColAttribute**を呼び出すサーバーのラウンドトリップは含まれません。  
  
> [!NOTE]  
>  すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の結果セットで、ODBC 列の ID 属性は使用できません。  
  
|フィールド ID|説明|  
|----------------------|-----------------|  
|SQL_COLUMN_TABLE_NAME|サーバー カーソルを生成するステートメントから取得した結果セットで使用できます。または、FOR BROWSE 句を含む実行済みの SELECT ステートメントで使用できます。|  
|SQL_DESC_BASE_COLUMN_NAME|サーバー カーソルを生成するステートメントから取得した結果セットで使用できます。または、FOR BROWSE 句を含む実行済みの SELECT ステートメントで使用できます。|  
|SQL_DESC_BASE_TABLE_NAME|サーバー カーソルを生成するステートメントから取得した結果セットで使用できます。または、FOR BROWSE 句を含む実行済みの SELECT ステートメントで使用できます。|  
|SQL_DESC_CATALOG_NAME|データベース名。 サーバー カーソルを生成するステートメントから取得した結果セットで使用できます。または、FOR BROWSE 句を含む実行済みの SELECT ステートメントで使用できます。|  
|SQL_DESC_LABEL|すべての結果セットで使用できます。 値は、SQL_DESC_NAME フィールドの値と等しくなります。<br /><br /> 列が式の結果か、式にラベル割り当てが含まれていない場合にのみ、フィールド長が 0 (ゼロ) になります。|  
|SQL_DESC_NAME|すべての結果セットで使用できます。 値は、SQL_DESC_LABEL フィールドの値と等しくなります。<br /><br /> 列が式の結果か、式にラベル割り当てが含まれていない場合にのみ、フィールド長が 0 (ゼロ) になります。|  
|SQL_DESC_SCHEMA_NAME|所有者名。 サーバー カーソルを生成するステートメントから取得した結果セットで使用できます。または、FOR BROWSE 句を含む実行済みの SELECT ステートメントで使用できます。<br /><br /> SELECT ステートメントの列に所有者名を指定した場合にのみ使用できます。|  
|SQL_DESC_TABLE_NAME|サーバー カーソルを生成するステートメントから取得した結果セットで使用できます。または、FOR BROWSE 句を含む実行済みの SELECT ステートメントで使用できます。|  
|SQL_DESC_UNNAMED|結果セット内にあるすべての列に対する SQL_NAMED が返されます。ただしこれは、式の一部にラベル割り当てが含まれておらず、列がこの式の結果ではない場合に限ります。 SQL_DESC_UNNAMED が SQL_UNNAMED を返すときは、すべての ODBC 列の ID 属性には、その列に対して長さゼロの文字列が含まれます。|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーは、準備済みで実行されていないステートメントに対して**SQLColAttribute**が呼び出されたときに、サーバーのオーバーヘッドを削減するために SET FMTONLY ステートメントを使用します。  
  
 大きな値型の場合 **、SQLColAttribute**は次の値を返します。  
  
|フィールド ID|変更の説明|  
|----------------------|---------------------------|  
|SQL_DESC_DISPLAY_SIZE|列のデータを表示する場合に必要となる最大文字数です。 大きな値型の列の場合、返される値は SQL_SS_LENGTH_UNLIMITED です。|  
|SQL_DESC_LENGTH|結果セット内の列の実際の長さを返します。 大きな値型の列の場合、返される値は SQL_SS_LENGTH_UNLIMITED です。|  
|SQL_DESC_OCTET_LENGTH|大きな値型の列の最大長を返します。 無制限のサイズを示す場合、SQL_SS_LENGTH_UNLIMITED を使用します。|  
|SQL_DESC_PRECISION|大きな値型の列の場合、値 SQL_SS_LENGTH_UNLIMITED を返します。|  
|SQL_DESC_TYPE|大きな値型の場合、SQL_VARCHAR、SQL_WVARCHAR、および SQL_VARBINARY を返します。|  
|SQL_DESC_TYPE_NAME|大きな値型の場合、"varchar"、"varbinary"、"nvarchar" を返します。|  
  
 すべてのバージョンで、準備された SQL ステートメントのバッチによって複数の結果セットが生成されるときは、最初の結果セットのみの列属性が報告されます。  
  
 次の列属性は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント ODBC ドライバーによって公開される拡張機能です。 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ODBC ドライバーは、すべての値を返す、 *NumericAttrPtr*パラメーターです。 WORD 配列へのポインターである SQL_CA_SS_COMPUTE_BYLIST を除き、SDWORD 型 (符号付き long 型) として値が返されます。  
  
|フィールド ID|返される値|  
|----------------------|--------------------|  
|SQL_CA_SS_COLUMN_HIDDEN*|参照される列が、FOR BROWSE 句を含む Transact-SQL SELECT ステートメントをサポートするために作成された非表示の主キーの一部である場合は、TRUE になります。|  
|SQL_CA_SS_COLUMN_ID|現在の Transact-SQL SELECT ステートメント内にある COMPUTE 句の結果列の序数位置。|  
|SQL_CA_SS_COLUMN_KEY*|参照される列が行の主キーの一部で、Transact-SQL SELECT ステートメントに FOR BROWSE 句が含まれる場合は、TRUE になります。|  
|SQL_CA_SS_COLUMN_OP|COMPUTE 句列の値に関連する集計演算子を指定する整数。 整数値の定義は sqlncli.h にあります。|  
|SQL_CA_SS_COLUMN_ORDER|ODBC または Transact-SQL SELECT ステートメントの ORDER BY 句内にある列の序数位置。|  
|SQL_CA_SS_COLUMN_SIZE|列から取得したデータ値を SQL_C_BINARY 変数にバインドするのに必要な、バイト単位の最大長。|  
|SQL_CA_SS_COLUMN_SSTYPE|SQL Server の列に格納されたデータのネイティブ データ型。 型値の定義は sqlncli.h にあります。|  
|SQL_CA_SS_COLUMN_UTYPE|SQL Server における列のユーザー定義データ型に関する基本データ型。 型値の定義は sqlncli.h にあります。|  
|SQL_CA_SS_COLUMN_VARYLEN|列のデータが可変長の場合は TRUE、それ以外の場合は FALSE です。|  
|SQL_CA_SS_COMPUTE_BYLIST|COMPUTE 句の BY 句で使用される列を指定する、WORD 型 (符号なし short 型) の配列へのポインター。 COMPUTE 句に BY が指定されていない場合、NULL ポインターを返します。<br /><br /> 配列の最初の要素には、BY リスト列の数が含まれます。 もう 1 つの要素は列序数です。|  
|SQL_CA_SS_COMPUTE_ID|現在の Transact-SQL SELECT ステートメントの COMPUTE 句の結果である行の*計算 ID。*|  
|SQL_CA_SS_NUM_COMPUTES|現在の Transact-SQL SELECT ステートメントで指定されている COMPUTE 句の数。|  
|SQL_CA_SS_NUM_ORDERS|ODBC または Transact-SQL SELECT ステートメントの ORDER BY 句で指定されている列の数。|  
  
 \*ステートメント属性SQL_SOPT_SS_HIDDEN_COLUMNSがSQL_HC_ON に設定されている場合に使用可能です。  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]は、XML スキーマ コレクション名、スキーマ名、およびカタログ名を示す追加情報を提供する、ドライバー固有の記述子フィールドを導入しました。 これらのプロパティでは、英数字以外の文字が含まれる場合でも、引用符やエスケープ文字は必要ありません。 次の表では、追加された新しい記述子フィールドについて説明します。  
  
|列名|Type|説明|  
|-----------------|----------|-----------------|  
|SQL_CA_SS_XML_SCHEMACOLLECTION_CATALOG_NAME|CharacterAttributePtr|XML スキーマ コレクション名が定義されているカタログの名前です。 カタログ名が見つからない場合は、この変数に空文字列が含まれます。<br /><br /> この情報は、IRD の SQL_DESC_SS_XML_SCHEMACOLLECTION_CATALOG_NAME レコード フィールドから返されます。このレコード フィールドは読み取りと書き込みが可能なフィールドです。|  
|SQL_CA_SS_XML_SCHEMACOLLECTION_SCHEMA_NAM E|CharacterAttributePtr|XML スキーマ コレクション名が定義されているスキーマの名前です。 スキーマ名が見つからない場合は、この変数に空文字列が含まれます。<br /><br /> この情報は、IRD の SQL_DESC_SS_XML_SCHEMACOLLECTION_SCHEMA_NAME レコード フィールドから返されます。このレコード フィールドは読み取りと書き込み可能なフィールドです。|  
|SQL_CA_SS_XML_SCHEMACOLLECTION_NAME|CharacterAttributePtr|XML スキーマ コレクションの名前です。 名前が見つからない場合は、この変数に空文字列が含まれます。<br /><br /> この情報は、IRD の SQL_DESC_SS_XML_SCHEMACOLLECTION_NAME レコード フィールドから返されます。このレコード フィールドは読み取りと書き込み可能なフィールドです。|  
  
 また、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] では、結果セットのユーザー定義型 (UDT) 列に関する追加情報、またはストアド プロシージャやパラメーター化クエリの UDT パラメーターに関する追加情報を提供するために、ドライバー固有の新しい記述子フィールドが導入されました。 これらのプロパティでは、英数字以外の文字が含まれる場合でも、引用符やエスケープ文字は必要ありません。 次の表では、追加された新しい記述子フィールドについて説明します。  
  
|列名|Type|説明|  
|-----------------|----------|-----------------|  
|SQL_CA_SS_UDT_CATALOG_NAME|CharacterAttributePtr|UDT を含むカタログの名前。|  
|SQL_CA_SS_UDT_SCHEMA_NAME|CharacterAttributePtr|UDT を含むスキーマの名前。|  
|SQL_CA_SS_UDT_TYPE_NAME|CharacterAttributePtr|UDT の名前|  
|SQL_CA_SS_UDT_ASSEMBLY_TYPE_NAME|CharacterAttributePtr|UDT のアセンブリ修飾名。|  
  
 UDT の名前を示すために、既存の記述子フィールド ID の SQL_DESC_TYPE_NAME が使用されます。 UDT 型の列の SQL_DESC_TYPE フィールドは SQL_SS_UDT です。  
  
## <a name="sqlcolattribute-support-for-enhanced-date-and-time-features"></a>SQLColAttribute による機能強化された日付と時刻のサポート  
 日付/時刻型の値が返される場合は、「[パラメータおよび結果メタデータ](../../relational-databases/native-client-odbc-date-time/metadata-parameter-and-result.md)」の「IRD フィールドに返される情報」セクションを参照してください。  
  
 詳細については、「 [ODBC&#41;&#40;日付と時刻の向上](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)」を参照してください。  
  
## <a name="sqlcolattribute-support-for-large-clr-udts"></a>SQLColAttribute による大きな CLR UDT のサポート  
 **大規模**な CLR ユーザー定義型 (UDT) をサポートしています。 詳細については、「 [ODBC&#41;&#40;大規模な CLR ユーザー定義型](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)」を参照してください。  
  
## <a name="sqlcolattribute-support-for-sparse-columns"></a>SQLColAttribute によるスパース列のサポート  
 SQLColAttribute は、新しい実装行記述子 (IRD) フィールドSQL_CA_SS_IS_COLUMN_SET照会して、列が**column_set**列かどうかを判断します。  
  
 詳細については、「 [ODBC&#41;の &#40;のスパース列のサポート](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [関数](https://go.microsoft.com/fwlink/?LinkId=59334)   
 [ODBC API の実装の詳細](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)  
  
  
