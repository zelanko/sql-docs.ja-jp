---
title: "setAsciiStream (int, java.io.InputStream) メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02c2443d-44e1-4f16-a0d5-08d197838214
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2d3931ee99e966d9359b78db7d05f82173d3c750
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setasciistream-method-int-javaioinputstream"></a>setAsciiStream (int, java.io.InputStream) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された java.io.InputStream オブジェクトを指定されたパラメーター数を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setAsciiStream(int parameterIndex,  
                                 java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *parameterIndex*  
  
 **Int**パラメーター数を示すです。  
  
 *x*  
  
 Java.io.InputStream オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setAsciiStream メソッドは、java.sql.PreparedStatement インターフェイスの setAsciiStream メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [setAsciiStream メソッド & #40 です。SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/setasciistream-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
