---
title: "getIndexInfo メソッド (SQLServerDatabaseMetaData) |Microsoft ドキュメント"
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
- SQLServerDatabaseMetaData.getIndexInfo
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8a677cc6-8e33-4e57-8678-0849345aa8d0
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 028937d023b6cf899eb5fa47354cb0c5d21545bc
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getindexinfo-method-sqlserverdatabasemetadata"></a>getIndexInfo メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡されたテーブルのインデックスと統計情報についての記述を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.ResultSet getIndexInfo(java.lang.String cat,  
                                       java.lang.String schema,  
                                       java.lang.String table,  
                                       boolean unique,  
                                       boolean approximate)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *cat*  
  
 A**文字列**カタログ名を格納しています。  
  
 *スキーマ*  
  
 A**文字列**スキーマ名を格納しています。  
  
 *テーブル*  
  
 A**文字列**テーブル名を格納しています。  
  
 *一意*  
  
 **true**のみ場合、一意の値のインデックスが返されます。 **false**のすべてのインデックスが返される場合。  
  
 *概数*  
  
 **true**場合は、結果に概数または期限切れの値が反映されます。 **false**結果が正確である場合。  
  
## <a name="return-value"></a>戻り値  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getIndexInfo メソッドは、java.sql.DatabaseMetaData インターフェイスの getIndexInfo メソッドによって指定されます。  
  
 GetIndexInfo メソッドによって返される結果セットには、次の情報が含まれます。  
  
|名前|型|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**文字列**|指定したテーブルが存在するデータベースの名前。|  
|TABLE_SCHEM|**文字列**|テーブルのスキーマです。|  
|TABLE_NAME|**文字列**|テーブルの名前です。|  
|NON_UNIQUE|**boolean**|インデックス値が重複可能であるかどうかを示します。|  
|INDEX_QUALIFIER|**文字列**|インデックスの所有者の名前。 TYPE が tableIndexStatistic の場合は null になります。|  
|INDEX_NAME|**文字列**|インデックスの名前。|  
|TYPE|**短い**|インデックスの種類。 次の値のいずれかを指定できます。<br /><br /> tableIndexStatistic (0)<br /><br /> tableIndexClustered (1)<br /><br /> tableIndexHashed (2)<br /><br /> tableIndexOther (3)|  
|ORDINAL_POSITION|**短い**|インデックス内での列の位置を示す序数です。 インデックスの最初の列は 1 です。|  
|COLUMN_NAME|**文字列**|列の名前です。|  
|ASC_OR_DESC|**文字列**|インデックスの照合で使用される順序です。 次の値のいずれかを指定できます。<br /><br /> A (昇順)<br /><br /> D (降順)<br /><br /> NULL (適用なし)<br /><br /> **注:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]常に"A"を返します。  |  
|CARDINALITY|**int**|テーブル内の行数またはインデックス内の一意の値の個数です。|  
|PAGES|**int**|インデックスまたはテーブルの格納に使用するページ数です。|  
|FILTER_CONDITION|**文字列**|フィルター条件です。<br /><br /> **注:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]常に null を返します。  |  
  
> [!NOTE]  
>  GetIndexInfo メソッドによって返されるデータに関する詳細については、「sp_indexes (TRANSACT-SQL)」を参照してください[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="example"></a>例  
 次の例では、インデックスと内の Person.Contact テーブルの統計に関する情報を返す getIndexInfo メソッドを使用して、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)]サンプル データベース。  
  
```  
public static void executeGetIndexInfo(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getIndexInfo("AdventureWorks", "Person", "Contact", false, true);  
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
  
  

