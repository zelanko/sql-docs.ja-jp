---
title: setNull (int、int, java.lang.String) メソッド |Microsoft ドキュメント
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
- SQLServerPreparedStatement.setNull (int, int, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 43c74e06-2858-49ba-bae7-b88808e5fff4
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a34ce8e9c268e810c09b6f39d940d27df866a3a8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="setnull-method-int-int-javalangstring"></a>setNull (int, int, java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡されたパラメーターの型と名前を使用して、指定されたパラメーターを null 値に設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setNull(int paramIndex,  
                          int sqlType,  
                          java.lang.String typeName)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *paramIndex*  
  
 **Int**パラメーター数を示すです。  
  
 *SQLtype*  
  
 Java.sql.Types で定義されている JDBC 型コード。  
  
 *typeName*  
  
 A**文字列**が設定されているパラメーターの完全修飾名を示すです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setNull メソッドは、java.sql.PreparedStatement インターフェイスの setNull メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [setNull メソッド&#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setnull-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
