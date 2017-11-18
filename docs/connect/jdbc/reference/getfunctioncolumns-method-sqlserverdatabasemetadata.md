---
title: "getFunctionColumns メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2b0e0f7-717c-48e6-bcd2-a325d938a833
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1508d70610c47116a4aaf58063b0f4196459d3e4
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getfunctioncolumns-method-sqlserverdatabasemetadata"></a>getFunctionColumns メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたカタログのシステム関数またはユーザー関数のパラメーターと戻り値の型に関する記述を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public ResultSet getFunctionColumns(java.lang.String catalog,  
                       java.lang.String schemaPattern,  
                       java.lang.String functionNamePattern  
                       java.lang.String columnNamePattern)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *カタログ*  
  
 A**文字列**カタログ名を格納しています。 空の文字列 "" の場合、結果にはカタログのない関数が含まれます。 場合は**null**検索、カタログ名は使用されません。  
  
 *schemaPattern*  
  
 A**文字列**スキーマ名のパターンを格納しています。 空の文字列 "" の場合、結果にはスキーマのない関数が含まれます。 場合は**null**検索、スキーマ名は使用されません。  
  
 *functionNamePattern*  
  
 A**文字列**関数の名前を格納しています。  
  
 *columnNamePattern*  
  
 A**文字列**パラメーターの名前を格納しています。  
  
## <a name="return-value"></a>戻り値  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getFunctionColumns メソッドは、java.sql.DatabaseMetaData インターフェイスの getFunctionColumns メソッドによって指定されます。  
  
 このメソッドは、指定されたカタログ内の指定されたスキーマ、関数名、およびパラメーター名に一致する関数およびパラメーターだけを返します。  
  
 結果セットの各行には、パラメーターの説明、列の説明、または戻り値の型に対する次の列が含まれます。  
  
|名前|型|Description|  
|----------|----------|-----------------|  
|FUNCTION_CAT|**文字列**|関数が存在するデータベースの名前です。|  
|FUNCTION_SCHEM|**文字列**|関数のスキーマです。|  
|FUNCTION_NAME|**文字列**|関数の名前です。|  
|COLUMN_NAME|**文字列**|パラメーターまたは列の名前です。|  
|COLUMN_TYPE|**短い**|**列の型。次の値のいずれかを指定できます。**<br /><br /> functionColumnUnknown (0): 不明な型です。<br /><br /> functionColumnIn (1): 入力パラメーターです。<br /><br /> functionColumnInOut (2): 入力/出力パラメーターです。<br /><br /> functionColumnOut (3): 出力パラメーターです。<br /><br /> functionReturn (4): 関数の戻り値です。<br /><br /> functionColumnResult (5): パラメーターまたは列は結果セット内の列です。|  
|DATA_TYPE|**smallint**|SQL データは、Java.sql.Types から値を入力します。|  
|TYPE_NAME|**文字列**|データ型の名前です。|  
|PRECISION|**int**|有効桁数の合計数。|  
|LENGTH|**int**|データの長さです (バイト)。|  
|SCALE|**短い**|小数点以下の桁数です。|  
|RADIX|**短い**|数値型の基数。|  
|NULLABLE|**短い**|パラメーターまたは戻り値を含めることができるかどうかを示します、 **null**値。<br /><br /> **次の値のいずれかを指定できます。**<br /><br /> functionNoNulls (0): NULL 値は許可されません。<br /><br /> functionNullable (1): NULL 値は許可されます。<br /><br /> functionNullableUnknown (2): 不明です。|  
|REMARKS|**文字列**|列またはパラメーターに関するコメントです。|  
|COLUMN_DEF|**文字列**|列の既定値です。<br /><br /> **注:**この情報で利用可能な[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]およびは JDBC driver に固有です。|  
|SQL_DATA_TYPE|**smallint**|この列は、同じ、 **DATA_TYPE**列を除き、 **datetime**と ISO**間隔**データ型。<br /><br /> **注:**この情報で利用可能な[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]およびは JDBC driver に固有です。|  
|SQL_DATETIME_SUB|**smallint**|**Datetime** ISO**間隔**サブコードの場合の値**SQL_DATA_TYPE**は**SQL_DATETIME**または**SQL_INTERVAL**. 型のデータ型以外の**datetime**と ISO**間隔**、この列は NULL です。<br /><br /> **注:**この情報で利用可能な[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]およびは JDBC driver に固有です。|  
|CHAR_OCTET_LENGTH|**int**|パラメーターまたは列に基づいたバイナリおよび文字の最大長です。 他のデータ型の場合は NULL です。|  
|ORDINAL_POSITION|**int**|入力パラメーターおよび出力パラメーターの場合は、1 から始まる位置を表します。<br /><br /> 結果セット列の場合は、1 から始まる結果セット内の列の位置です。<br /><br /> 戻り値の場合は 0 です。|  
|IS_NULLABLE|**文字列**|パラメーターまたは列で null 値が許可されるかどうかを決定します。<br /><br /> 次の値のいずれかを指定できます。<br /><br /> **[はい]**: パラメーターまたは列が NULL 値を含めることができます。<br /><br /> **いいえ**: パラメーターまたは列が NULL 値を含まれません。<br /><br /> 空の文字列 (""): 不明です。|  
|SS_TYPE_CATALOG_NAME|**文字列**|ユーザー定義型 (UDT) を含むカタログの名前。|  
|SS_TYPE_SCHEMA_NAME|**文字列**|UDT (ユーザー定義型) を含むスキーマの名前です。|  
|SS_UDT_CATALOG_NAME|**文字列**|完全修飾名の UDT (ユーザー定義型) です。|  
|SS_UDT_SCHEMA_NAME|**文字列**|XML スキーマ コレクション名が定義されているカタログの名前です。 カタログ名が見つからない場合、この変数には、空の文字列が含まれています。|  
|SS_UDT_ASSEMBLY_TYPE_NAME|**文字列**|XML スキーマ コレクション名が定義されているスキーマの名前です。 スキーマ名が見つからない場合は、空文字列です。|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|**文字列**|XML スキーマ コレクションの名前です。 名前が見つからない場合は、空文字列です。|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|**文字列**|ユーザー定義型 (UDT) を含むカタログの名前。|  
|SS_XML_SCHEMACOLLECTION_NAME|**文字列**|UDT (ユーザー定義型) を含むスキーマの名前です。|  
|SS_DATA_TYPE|**tinyint**|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]拡張ストアド プロシージャによって使用されるデータ型。<br /><br /> **注**によって返されるデータ型の詳細については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]、「データ型 (TRANSACT-SQL)」を参照してください[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]オンライン ブック。|  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

