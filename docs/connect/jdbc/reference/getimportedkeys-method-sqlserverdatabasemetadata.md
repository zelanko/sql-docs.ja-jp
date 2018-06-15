---
title: getImportedKeys メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント
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
- SQLServerDatabaseMetaData.getImportedKeys
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dc8c1a5e-700e-4059-a5ed-5013bbb87fb6
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de5ae39ff10c32737df637c9a6f29aab19d27574
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32836687"
---
# <a name="getimportedkeys-method-sqlserverdatabasemetadata"></a>getImportedKeys メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  テーブル内の外部キー列によって参照される、主キー列の記述を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.ResultSet getImportedKeys(java.lang.String cat,  
                                          java.lang.String schema,  
                                          java.lang.String table)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *cat*  
  
 A**文字列**カタログ名を格納しています。  
  
 *schema*  
  
 A**文字列**スキーマ名を格納しています。  
  
 *テーブル*  
  
 A**文字列**テーブル名を格納しています。  
  
## <a name="return-value"></a>戻り値  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getImportedKeys メソッドは、java.sql.DatabaseMetaData インターフェイスの getImportedKeys メソッドによって指定されます。  
  
 GetImportedKeys メソッドによって返される結果セットには、次の情報が含まれます。  
  
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
|KEY_SEQ|**short**|複数列の主キーにおける列のシーケンス番号です。|  
|UPDATE_RULE|**short**|SQL の操作が更新プログラムのとき、外部キーに適用されるアクション。 次の値のいずれかを指定できます。<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|DELETE_RULE|**short**|SQL の操作が削除であるとき、外部キーに適用されるアクション。 次の値のいずれかを指定できます。<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|FK_NAME|**文字列**|外部キーの名前です。|  
|PK_NAME|**文字列**|主キーの名前です。|  
|DEFERRABILITY|**short**|外部キーの制限の評価を、コミット時まで遅延できるかどうかを示します。 次の値のいずれかを指定できます。<br /><br /> importedKeyInitiallyDeferred (5)<br /><br /> importedKeyInitiallyImmediate (6)<br /><br /> importedKeyNotDeferrable (7)|  
  
> [!NOTE]  
>  GetImportedKeys メソッドによって返されるデータに関する詳細については、「sp_fkeys (TRANSACT-SQL)」を参照してください[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="example"></a>例  
 次の例では、Person.Address テーブルの外部キーを参照するすべてのプライマリ キーに関する情報を返す getImportedKeys メソッドを使用して、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]サンプル データベース。  
  
```  
public static void executeGetImportedKeys(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getImportedKeys("AdventureWorks", "Person", "Address");  
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
  
  
