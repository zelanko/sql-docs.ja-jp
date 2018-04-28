---
title: getAsciiStream (int) |Microsoft ドキュメント
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
- SQLServerCallableStatement.getAsciiStream(int paramIndex)
apilocation:
- SQLServerCallableStatement.getAsciiStream(int paramIndex)
apitype: Assembly
ms.assetid: 9d8b235e-4208-40ee-b5a5-bc76f73b82f8
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 17ed8f35c1bbcbee9df2d25efb6544edf8d8be6d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="getasciistream-int"></a>getAsciiStream (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターの値のストリームとして取得**ASCII**パラメーター インデックスを指定した文字。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final java.io.InputStream getAsciiStream(int paramIndex)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *paramIndex*  
  
 **Int**パラメーター インデックスを示すです。  
  
## <a name="return-value"></a>戻り値  
 InputStream オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="see-also"></a>参照  
 [getAsciiStream メソッド&#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getasciistream-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
