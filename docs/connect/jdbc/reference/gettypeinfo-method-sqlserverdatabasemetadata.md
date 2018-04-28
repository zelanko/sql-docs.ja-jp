---
title: getTypeInfo メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.getTypeInfo
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 23208f01-c1bf-4235-b29c-9051d3df59a3
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 032ddf6a5f266fa68c6a735dd7f59cf4df02c68e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="gettypeinfo-method-sqlserverdatabasemetadata"></a>getTypeInfo メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  現在のデータベースによってサポートされる、すべての標準 SQL 型に関する記述を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.ResultSet getTypeInfo()  
```  
  
## <a name="return-value"></a>戻り値  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getTypeInfo メソッドは、java.sql.DatabaseMetaData インターフェイスの getTypeInfo メソッドによって指定されます。  
  
 GetTypeInfo メソッドによって返される結果セットには、次の情報が含まれます。  
  
|名前|型|Description|  
|----------|----------|-----------------|  
|TYPE_NAME|**文字列**|データ型の名前です。|  
|DATA_TYPE|**short**|java.sql.Types の SQL データ型です。|  
|PRECISION|**int**|有効桁数の合計数。|  
|LITERAL_PREFIX|**文字列**|文字または文字定数の前に使用します。|  
|LITERAL_SUFFIX|**文字列**|文字または文字定数を終了するために使用します。|  
|CREATE_PARAMS|**文字列**|データ型の作成パラメーターの記述です。|  
|NULLABLE|**short**|列に null 値を含めることができるかどうかを示します。 次の値のいずれかを指定できます。<br /><br /> typeNoNulls (0)<br /><br /> typeNullable (1)<br /><br /> typeNullableUnknown (2)|  
|CASE_SENSITIVE|**boolean**|データ型の大文字と小文字を区別するかどうかを示します。 "**true**「型が大文字小文字を区別、それ以外の場合」**false**"です。|  
|SEARCHABLE|**short**|列を SQL の WHERE 句で使用できるかどうかを示します。 次の値のいずれかを指定できます。<br /><br /> typePredNone (0)<br /><br /> typePredChar (1)<br /><br /> typePredBasic (2)<br /><br /> typeSeachable (3)|  
|UNSIGNED_ATTRIBUTE|**boolean**|データ型の符号を示します。 "**true**「型が符号なし、それ以外の場合」**false**"です。|  
|FIXED_PREC_SCALE|**boolean**|データ型に money 値を指定できるかどうかを示します。 "**true**"データ型は money 型である場合は、それ以外の場合、"**false**"です。|  
|AUTO_INCREMENT|**boolean**|データ型を自動インクリメントできるかどうかを示します。 "**true**"場合は、型を自動的には、インクリメント、それ以外の"**false**"です。|  
|LOCAL_TYPE_NAME|**文字列**|データ型のローカライズされた名前です。|  
|MINIMUM_SCALE|**short**|小数点以下の最大桁数です。|  
|MAXIMUM_SCALE|**short**|小数点以下の最小桁数です。|  
|SQL_DATA_TYPE|**int**|JDBC ドライバーではサポートされていません。|  
|SQL_DATETIME_SUB|**int**|JDBC ドライバーではサポートされていません。|  
|NUM_PREC_RADIX|**int**|列が保持できる最大数を計算する場合のビット数または桁数です。|  
|INTERVAL_PRECISION|**smallint**|期間の先頭の有効桁数の値です。|  
|USERTYPE|**smallint**|**Usertype**値から、 **systypes**テーブル。 詳細については、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] オンライン ブックを参照してください。|  
  
> [!NOTE]  
>  GetTypeInfo メソッドによって返されるデータに関する詳細については、「sp_datatype_info (TRANSACT-SQL)」を参照してください[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="example"></a>例  
 次の例で使用されるデータ型に関する情報を返す getTypeInfo メソッドを使用して、 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005_md.md)] (またはそれ以降) データベース。  
  
```  
public static void executeGetTypeInfo(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getTypeInfo();  
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
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
