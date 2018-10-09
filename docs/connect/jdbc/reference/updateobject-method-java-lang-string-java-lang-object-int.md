---
title: setObject メソッド (java.lang.String, java.lang.Object, int) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateObject (java.lang.String, java.lang.Object, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 27283ce1-637e-4e2c-91ee-8ad379114ac5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10959976eb6c3c9908d7f5953a8a2edb1c1328c8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47654918"
---
# <a name="updateobject-method-javalangstring-javalangobject-int"></a>updateObject (java.lang.String, java.lang.Object, int) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された列インデックスおよび小数点以下桁数を使用して、指定された列を **Object** 値で更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateObject(java.lang.String columnName,  
                         java.lang.Object x,  
                         int scale)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 列名を含む**文字列**です。  
  
 *obj*  
  
 **Object** 値。  
  
 *scale*  
  
 java.sql.Types.DECIMAL 型または java.sql.Types.NUMERIC 型の場合、この値は小数点以下の桁数になります。 他のすべての型については、この値は無視されます。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この updateObject メソッドは、java.sql.ResultSet インターフェイスに updateObject メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [updateObject メソッド &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateobject-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
