---
title: "getColumnType メソッド (SQLServerResultSetMetaData) |Microsoft ドキュメント"
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
- SQLServerResultSetMetaData.getColumnType
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 81815a41-9265-4574-a4d8-f6341a68d9fd
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ad090a3ad5377be43f0c91febb79cfbfc56b5330
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getcolumntype-method-sqlserverresultsetmetadata"></a>getColumnType メソッド (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列の SQL 型を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getColumnType(int column)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *列*  
  
 **Int**列インデックスを示すです。  
  
## <a name="return-value"></a>戻り値  
 **Int** java.sql.Types で定義されている JDBC の型を示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getColumnType メソッドは、java.sql.ResultSetMetaData インターフェイスの getColumnType メソッドによって指定されます。  
  
 [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] JDBC Driver 3.0 は、DATA_TYPE 列の動作の変更がします。 参照してください[SQLServerDatabaseMetaData.getColumns](../../../connect/jdbc/reference/getcolumns-method-sqlserverdatabasemetadata.md)詳細についてはします。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSetMetaData のメンバー](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData クラス](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  

