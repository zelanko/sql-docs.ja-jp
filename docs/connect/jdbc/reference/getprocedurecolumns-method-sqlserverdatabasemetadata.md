---
title: "getProcedureColumns メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.getProcedureColumns
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4f0df8fe-3cd6-46e4-ae3c-dc23c35676b2
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 847a037a1721e6ecd517d78f99d96b0ef2754aba
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getprocedurecolumns-method-sqlserverdatabasemetadata"></a>getProcedureColumns メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  ストアド プロシージャのパラメーターと結果列の記述を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.ResultSet getProcedureColumns(java.lang.String sCatalog,  
                                              java.lang.String sSchema,  
                                              java.lang.String proc,  
                                              java.lang.String col)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sCatalog*  
  
 A**文字列**カタログ名を格納しています。 このパラメーターに null を指定すると、カタログ名を使用する必要はありません。  
  
 *スキーマ*  
  
 A**文字列**スキーマ名のパターンを格納しています。 このパラメーターに null を指定すると、スキーマ名を使用する必要はありません。  
  
 *proc*  
  
 A**文字列**プロシージャ名のパターンを格納しています。  
  
 *col*  
  
 A**文字列**列名のパターンを格納しています。 このパラメーターに null を指定すると、各列の行が返されます。  
  
## <a name="return-value"></a>戻り値  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getProcedureColumns メソッドは、java.sql.DatabaseMetaData インターフェイスの getProcedureColumns メソッドによって指定されます。  
  
 GetProcedureColumns メソッドによって返される結果セットには、次の情報が含まれます。  
  
|名前|型|Description|  
|----------|----------|-----------------|  
|PROCEDURE_CAT|**文字列**|指定したストアド プロシージャが存在するデータベースの名前です。|  
|PROCEDURE_SCHEM|**文字列**|ストアド プロシージャのスキーマです。|  
|PROCEDURE_NAME|**文字列**|ストアド プロシージャの名前です。|  
|COLUMN_NAME|**文字列**|列の名前です。|  
|COLUMN_TYPE|**短い**|列の型。 次の値のいずれかを指定できます。<br /><br /> procedureColumnUnknown (0)<br /><br /> procedureColumnIn (1)<br /><br /> procedureColumnInOut (2)<br /><br /> procedureColumnOut (4)<br /><br /> procedureColumnReturn (5)<br /><br /> procedureColumnResult (3)|  
|DATA_TYPE|**smallint**|java.sql.Types の SQL データ型です。|  
|TYPE_NAME|**文字列**|データ型の名前です。|  
|PRECISION|**int**|有効桁数の合計数。|  
|LENGTH|**int**|データの長さです (バイト)。|  
|SCALE|**短い**|小数点以下の桁数です。|  
|RADIX|**短い**|数値型の基数。|  
|NULLABLE|**短い**|列に null 値を含めることができるかどうかを示します。 次の値のいずれかを指定できます。<br /><br /> procedureNoNulls (0)<br /><br /> procedureNullable (1)<br /><br /> procedureNullableUnknown (2)|  
|REMARKS|**文字列**|プロシージャ列の記述です。<br /><br /> <br /><br /> **注:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]はこの列の値を返しません。|  
|COLUMN_DEF|**文字列**|列の既定値です。|  
|SQL_DATA_TYPE|**smallint**|この列は、同じ、 **DATA_TYPE**列を除き、 **datetime**と ISO**間隔**データ型。|  
|SQL_DATETIME_SUB|**smallint**|**Datetime** ISO**間隔**サブコードの場合の値**SQL_DATA_TYPE**は**SQL_DATETIME**または**SQL_INTERVAL**. 型のデータ型以外の**datetime**と ISO**間隔**、この列は NULL です。|  
|CHAR_OCTET_LENGTH|**int**|列の最大バイト数です。|  
|ORDINAL_POSITION|**int**|テーブル内の列のインデックスです。|  
|IS_NULLABLE|**文字列**|列で null 値が許容されるかどうかを示します。|  
|SS_TYPE_CATALOG_NAME|**文字列**|ユーザー定義型 (UDT) を含むカタログの名前。|  
|SS_TYPE_SCHEMA_NAME|**文字列**|UDT (ユーザー定義型) を含むスキーマの名前です。|  
|SS_UDT_CATALOG_NAME|**文字列**|完全修飾名の UDT (ユーザー定義型) です。|  
|SS_UDT_SCHEMA_NAME|**文字列**|XML スキーマ コレクション名が定義されているカタログの名前です。 カタログ名が見つからない場合、この変数には、空の文字列が含まれています。|  
|SS_UDT_ASSEMBLY_TYPE_NAME|**文字列**|XML スキーマ コレクション名が定義されているスキーマの名前です。 スキーマ名が見つからない場合は、空文字列です。|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|**文字列**|XML スキーマ コレクションの名前です。 名前が見つからない場合は、空文字列です。|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|**文字列**|ユーザー定義型 (UDT) を含むカタログの名前。|  
|SS_XML_SCHEMACOLLECTION_NAME|**文字列**|UDT (ユーザー定義型) を含むスキーマの名前です。|  
|SS_DATA_TYPE|**tinyint**|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]拡張ストアド プロシージャによって使用されるデータ型。<br /><br /> <br /><br /> **注:**によって返されるデータ型の詳細については[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]、「データ型 (TRANSACT-SQL)」を参照してください[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]オンライン ブック。|  
  
> [!NOTE]  
>  GetProcedureColumns メソッドによって返されるデータに関する詳細については、「sp_sproc_columns (TRANSACT-SQL)」を参照してください[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="example"></a>例  
 次の例で uspGetBillOfMaterials ストアド プロシージャに関する情報を返す getProcedureColumns メソッドを使用して、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]サンプル データベース。  
  
```  
public static void executeGetProcedureColumns(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getProcedureColumns(null, null, "uspGetBillOfMaterials", null);  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }   
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
