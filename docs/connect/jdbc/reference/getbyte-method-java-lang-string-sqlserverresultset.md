---
title: getByte (java.lang.String) メソッド (SQLServerResultSet) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLServerResultSet.getByte (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 069c68ff-442d-4104-917f-3445a3ad264a
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4aed20bd91fc430e7e4e8d591d19ecc0afb466c7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getbyte-method-javalangstring-sqlserverresultset"></a>getByte (java.lang.String) メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  この現在の行に指定された列名の値を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)オブジェクトとして、**バイト**java プログラミング言語です。  
  
## <a name="syntax"></a>構文  
  
```  
  
public byte getByte(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 A**文字列**列の名前を格納しています。  
  
## <a name="return-value"></a>戻り値  
 A**バイト**値。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getByte メソッドは、java.sql.ResultSet インターフェイスの getByte メソッドによって指定されます。  
  
 このメソッドでのみサポートされて[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]tinyint や bit などのバイト値を安全に返すことができるデータ型。 その他のデータ型では例外がスローされます。  
  
## <a name="see-also"></a>参照  
 [getByte メソッド&#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getbyte-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
