---
title: "getColumnDisplaySize メソッド (SQLServerResultSetMetaData) |Microsoft ドキュメント"
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
- SQLServerResultSetMetaData.getColumnDisplaySize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 21c25443-bd2b-4b60-9798-4efe2c158952
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 10eb09f395c661e7cc46629662d62e43bd937f05
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="getcolumndisplaysize-method-sqlserverresultsetmetadata"></a>getColumnDisplaySize メソッド (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された列の文字数で通常の最大の幅を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public int getColumnDisplaySize(int column)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *列*  
  
 **Int**列インデックスを示すです。  
  
## <a name="return-value"></a>戻り値  
 **Int**幅の最大値を示すです。 最大幅が不明の場合は、0 を返します。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getColumnDisplaySize メソッドは、java.sql.ResultSetMetaData インターフェイスの getColumnDisplaySize メソッドによって指定されます。  
  
 [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] JDBC Driver 3.0 は、COLUMN_SIZE 列の動作の変更がします。 参照してください[SQLServerDatabaseMetaData.getColumns](../../../connect/jdbc/reference/getcolumns-method-sqlserverdatabasemetadata.md)詳細についてはします。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSetMetaData のメンバー](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData クラス](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  

