---
title: getPrimaryKeys メソッド (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getPrimaryKeys
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ebfe236a-dc02-493e-a3ab-5353d3769e36
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bdb1eb0053c9bb15c6d03013df13635e022a5072
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67980766"
---
# <a name="getprimarykeys-method-sqlserverdatabasemetadata"></a>getPrimaryKeys メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡されたテーブルの主キー列の記述を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.ResultSet getPrimaryKeys(java.lang.String cat,  
                                         java.lang.String schema,  
                                         java.lang.String table)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *cat*  
  
 カタログ名を含む**文字列**です。  
  
 *schema*  
  
 スキーマ名を含む**文字列**です。  
  
 *テーブル*  
  
 テーブル名を含む**文字列**です。  
  
## <a name="return-value"></a>戻り値  
 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getPrimaryKeys メソッドは、java.sql.DatabaseMetaData インターフェイスの getPrimaryKeys メソッドで指定されています。  
  
 getPrimaryKeys メソッドによって返される結果セットには、次の情報が含まれます。  
  
|Name|種類|説明|  
|----------|----------|-----------------|  
|TABLE_CAT|String|指定したテーブルが含まれているデータベースの名前です。|  
|TABLE_SCHEM|String|テーブルのスキーマです。|  
|TABLE_NAME|String|テーブルの名前。|  
|COLUMN_NAME|String|列の名前です。|  
|KEY_SEQ|short|複数列の主キーにおける列のシーケンス番号です。|  
|PK_NAME|String|主キーの名前です。|  
  
> [!NOTE]  
>  getPrimaryKeys メソッドによって返されるデータの詳細については、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オンライン ブックの「sp_pkeys (Transact-SQL)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、getPrimaryKeys メソッドを使用して、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] サンプル データベースにある Person.Contact テーブルの主キーに関する情報を返す方法を示します。  
  
```  
public static void executeGetPrimaryKeys(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getPrimaryKeys("AdventureWorks", "Person", "Contact");  
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
  
  
