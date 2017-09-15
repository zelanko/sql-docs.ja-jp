---
title: "getTables メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
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
- SQLServerDatabaseMetaData.getTables
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a7514673-3457-4541-9560-28a8284ad9e3
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9bbf35aeec7b5626b380fc654995d181fe124811
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="gettables-method-sqlserverdatabasemetadata"></a>getTables メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡されたカタログ、スキーマ、またはテーブル名のパターンで使用可能なテーブルの記述を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.ResultSet getTables(java.lang.String catalog,  
                                    java.lang.String schema,  
                                    java.lang.String table,  
                                    java.lang.String[] types)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *カタログ*  
  
 A**文字列**カタログ名を格納しています。 このパラメーターに null を指定すると、カタログ名を使用する必要はありません。  
  
 *スキーマ*  
  
 A**文字列**スキーマ名のパターンを格納しています。 このパラメーターに null を指定すると、スキーマ名を使用する必要はありません。  
  
 *テーブル名*  
  
 A**文字列**テーブル名のパターンを格納しています。  
  
 *型*  
  
 含めるテーブルの型を含む文字列の配列です。 null は、すべての型のテーブルを含める必要があることを示します。  
  
## <a name="return-value"></a>戻り値  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getTables メソッドは、java.sql.DatabaseMetaData インターフェイスの getTables メソッドによって指定されます。  
  
 GetTables メソッドによって返される結果セットには、次の情報が含まれます。  
  
|名前|型|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**文字列**|指定したテーブルが存在するデータベースの名前。|  
|TABLE_SCHEM|**文字列**|テーブル スキーマ名です。|  
|TABLE_NAME|**文字列**|テーブル名。|  
|TABLE_TYPE|**文字列**|テーブルの型です。|  
|REMARKS|**文字列**|テーブルの説明です。<br /><br /> **注:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]はこの列の値を返しません。|  
|TYPE_CAT|**文字列**|JDBC ドライバーではサポートされていません。|  
|TYPE_SCHEM|**文字列**|JDBC ドライバーではサポートされていません。|  
|TYPE_NAME|**文字列**|JDBC ドライバーではサポートされていません。|  
|SELF_REFERENCING_COL_NAME|**文字列**|JDBC ドライバーではサポートされていません。|  
|REF_GENERATION|**文字列**|JDBC ドライバーではサポートされていません。|  
  
> [!NOTE]  
>  GetTables メソッドによって返されるデータの詳細についてを参照してください「sp_tables (TRANSACT-SQL)」[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="example"></a>例  
 次の例では、getTables メソッド内の Person.Contact テーブルのテーブル記述情報を使用して、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]サンプル データベース。  
  
```  
public static void executeGetTables(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getTables("AdventureWorks", "Person", "Contact", null);  
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
  
  
