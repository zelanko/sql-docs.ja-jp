---
title: getProcedures メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getProcedures
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 66c9a8b0-dc4c-4cbb-8004-c7157368cab4
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: df6101068f9d64ac243666d28c231c88a7926001
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32839257"
---
# <a name="getprocedures-method-sqlserverdatabasemetadata"></a>getProcedures メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡されたカタログ、スキーマ、またはストアド プロシージャ名のパターンで使用可能なストアド プロシージャの記述を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.ResultSet getProcedures(java.lang.String sCatalog,  
                                        java.lang.String sSchema,  
                                        java.lang.String proc)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sCatalog*  
  
 A**文字列**カタログ名を格納しています。 このパラメーターに null を指定すると、カタログ名を使用する必要はありません。  
  
 *スキーマ*  
  
 A**文字列**スキーマ名のパターンを格納しています。 このパラメーターに null を指定すると、スキーマ名を使用する必要はありません。  
  
 *proc*  
  
 A**文字列**プロシージャ名のパターンを格納しています。  
  
## <a name="return-value"></a>戻り値  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getProcedures メソッドは、java.sql.DatabaseMetaData インターフェイスの getProcedures メソッドによって指定されます。  
  
 GetProcedures メソッドによって返される結果セットには、次の情報が含まれます。  
  
|名前|型|Description|  
|----------|----------|-----------------|  
|PROCEDURE_CAT|**文字列**|指定したストアド プロシージャが存在するデータベースの名前です。|  
|PROCEDURE_SCHEM|**文字列**|ストアド プロシージャのスキーマです。|  
|PROCEDURE_NAME|**文字列**|ストアド プロシージャの名前です。|  
|NUM_INPUT_PARAMS|**int**|今後の使用のために予約されています。現在は -1 の値を返します。|  
|NUM_OUTPUT_PARAMS|**int**|今後の使用のために予約されています。現在は -1 の値を返します。|  
|NUM_RESULT_SETS|**int**|今後の使用のために予約されています。現在は -1 の値を返します。|  
|REMARKS|**文字列**|プロシージャ列の記述です。<br /><br /> <br /><br /> **注:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]はこの列の値を返しません。  |  
|PROCEDURE_TYPE|**smallint**|ストアド プロシージャの種類です。 次の値のいずれかを指定できます。<br /><br /> SQL_PT_UNKNOWN (0)<br /><br /> SQL_PT_PROCEDURE (1)<br /><br /> SQL_PT_FUNCTION (2)|  
  
> [!NOTE]  
>  GetProcedures メソッドによって返されるデータに関する詳細については、「sp_stored_procedures (TRANSACT-SQL)」を参照してください[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="example"></a>例  
 次の例で uspGetBillOfMaterials ストアド プロシージャに関する情報を返す、getProcedures メソッドを使用して、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]サンプル データベース。  
  
```  
public static void executeGetProcedures(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getProcedures(null, null, "uspGetBillOfMaterials");  
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
  
  
