---
title: "getCrossReference メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDatabaseMetaData.getCrossReference
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 099dd0bf-b017-479d-9696-f5b06f4c6bf9
caps.latest.revision: "15"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f97c43b92f6304cf2bb59f925933f57479132991
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="getcrossreference-method-sqlserverdatabasemetadata"></a>getCrossReference メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  主キー テーブルの主キー列を参照する外部キー テーブルの外部キー列の記述を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.ResultSet getCrossReference(java.lang.String cat1,  
                                            java.lang.String schem1,  
                                            java.lang.String tab1,  
                                            java.lang.String cat2,  
                                            java.lang.String schem2,  
                                            java.lang.String tab2)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *cat1*  
  
 A**文字列**プライマリ キーを含むテーブルのカタログ名を格納しています。  
  
 *schem1*  
  
 A**文字列**プライマリ キーを含むテーブルのスキーマ名を格納しています。  
  
 *tab1*  
  
 A**文字列**プライマリ キーを含むテーブルのテーブル名を格納しています。  
  
 *cat2*  
  
 A**文字列**外部キーを含むテーブルのカタログ名を格納しています。  
  
 *schem2*  
  
 A**文字列**外部キーを含むテーブルのスキーマ名を格納しています。  
  
 *tab2*  
  
 A**文字列**外部キーを含むテーブルのテーブル名を格納しています。  
  
## <a name="return-value"></a>戻り値  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getCrossReference メソッドは、java.sql.DatabaseMetaData インターフェイスの getCrossReference メソッドによって指定されます。  
  
 GetCrossReference メソッドによって返される結果セットには、次の情報が含まれます。  
  
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
>  GetCrossReference メソッドによって返されるデータに関する詳細については、「sp_fkeys (TRANSACT-SQL)」を参照してください[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="example"></a>例  
 次の例では、getCrossReference メソッドを使用して Person.Contact と HumanResources.Employee テーブル間で、主キーと外部キー リレーションシップに関する情報を取得する方法、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]サンプル データベース。  
  
```  
public static void executeGetCrossReference(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getCrossReference("AdventureWorks", "Person", "Contact", null, "HumanResources", "Employee");  
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
  
  
