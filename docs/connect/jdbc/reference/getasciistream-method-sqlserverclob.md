---
title: getAsciiStream メソッド (SQLServerClob) |Microsoft ドキュメント
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
- SQLServerClob.getAsciiStream
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 134abe5e-5add-4d27-b333-b4b0f4d94c31
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 601eb37aa51727d4b40ddc50bc80d9541cf456ae
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getasciistream-method-sqlserverclob"></a>getAsciiStream メソッド (SQLServerClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  CLOB を ASCII ストリームとして具体化します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.io.InputStream getAsciiStream()  
```  
  
## <a name="return-value"></a>戻り値  
 CLOB データを格納している入力ストリームです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getAsciiStream メソッドは、getAsciiStream、java.sql.Clob インターフェイスのメソッドでによって指定されます。  
  
 常にバイト ストリームを返し、CLOB 内のデータを ASCII 形式であると見なします。Unicode やその他のマルチバイト コード ページであるかどうかを認識する方法がないためです。  
  
## <a name="see-also"></a>参照  
 [SQLServerClob のメソッド](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob のメンバー](../../../connect/jdbc/reference/sqlserverclob-members.md)   
 [SQLServerClob クラス](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
