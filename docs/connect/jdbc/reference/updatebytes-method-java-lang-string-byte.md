---
title: "updateBytes メソッド (java.lang.String, byte) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerResultSet.updateBytes (java.lang.String, byte[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4fb9de2b-61bc-4c96-89a5-c07cd7ee201a
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 995ae6ccb99dcf1b982d4675697ca7e4953487a0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="updatebytes-method-javalangstring-byte"></a>updateBytes (java.lang.String, byte) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  配列で指定された列を更新**バイト**値列の名前を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateBytes(java.lang.String columnName,  
                        byte[] x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 A**文字列**列の名前を格納しています。  
  
 *x*  
  
 配列**バイト**値。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateBytes メソッドは、java.sql.ResultSet インターフェイスの updateBytes メソッドによって指定されます。  
  
 以前のバージョンで[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]、SQLServerResultSet.updateBytes を使用してバイト配列間の変換と[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データ型**日付**、**時間**、 **datetime2**、または**datetimeoffset**です。 新しいバージョンでは、これらのデータ型に対してこのメソッドを使用すると、変換がサポートされていないことを示す例外が発生します。  
  
## <a name="see-also"></a>参照  
 [updateBytes メソッド &#40;です。SQLServerResultSet &#41;](../../../connect/jdbc/reference/updatebytes-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

