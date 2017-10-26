---
title: "getExportedKeys メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
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
- SQLServerDatabaseMetaData.getExportedKeys
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 26888e61-b243-4a1b-922c-c0a451dcff4d
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e24d6268d5c46bb67b0ea97f593de1ccf7ec3f3c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getexportedkeys-method-sqlserverdatabasemetadata"></a>getExportedKeys メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたテーブルの主キー列を参照する外部キー列の記述を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.ResultSet getExportedKeys(java.lang.String cat,  
                                          java.lang.String schema,  
                                          java.lang.String table)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *cat*  
  
 A**文字列**カタログ名を格納しています。  
  
 *スキーマ*  
  
 A**文字列**スキーマ名を格納しています。  
  
 *テーブル*  
  
 A**文字列**テーブル名を格納しています。  
  
## <a name="return-value"></a>戻り値  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getExportedKeys メソッドは、java.sql.DatabaseMetaData インターフェイスの getExportedKeys メソッドによって指定されます。  
  
 GetExportedKeys メソッドによって返される結果セットには、次の情報が含まれます。  
  
|名前|型|Description|  
|----------|----------|-----------------|  
|PKTABLE_CAT|**文字列**|主キー テーブルを含むカタログの名前です。|  
|PKTABLE_SCHEM|**文字列**|主キー テーブルのスキーマの名前です。|  
|PKTABLE_NAME|**文字列**|主キー テーブルの名前です。|  
|PKCOLUMN_NAME|**文字列**|主キーの列名です。|  
|FKTABLE_CAT|**文字列**|外部キー テーブルを含むカタログの名前です。|  
|FKTABLE_SCHEM|**文字列**|外部キー テーブルのスキーマの名前です。|  
|FKTABLE_NAME|**文字列**|外部キー テーブルの名前です。|  
|FKCOLUMN_NAME|**文字列**|外部キーの列名です。|  
|KEY_SEQ|**短い**|複数列の主キーにおける列のシーケンス番号です。|  
|UPDATE_RULE|**短い**|SQL の操作が更新プログラムのとき、外部キーに適用されるアクション。 次の値のいずれかを指定できます。<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|DELETE_RULE|**短い**|SQL の操作が削除であるとき、外部キーに適用されるアクション。 次の値のいずれかを指定できます。<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|FK_NAME|**文字列**|外部キーの名前です。|  
|PK_NAME|**文字列**|主キーの名前です。|  
|DEFERRABILITY|**短い**|外部キーの制限の評価を、コミット時まで遅延できるかどうかを示します。 次の値のいずれかを指定できます。<br /><br /> importedKeyInitiallyDeferred (5)<br /><br /> importedKeyInitiallyImmediate (6)<br /><br /> importedKeyNotDeferrable (7)|  
  
> [!NOTE]  
>  GetExportedKeys メソッドによって返されるデータに関する詳細については、「sp_fkeys (TRANSACT-SQL)」を参照してください[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="example"></a>例  
 次の例では、Person.Contact テーブルの主キーを参照するすべての外部キーに関する情報を返す getExportedKeys メソッドを使用して、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]サンプル データベース。  
  
```  
public static void executeGetExportedKeys(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getExportedKeys("AdventureWorks", "Person", "Contact");  
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
  
  

