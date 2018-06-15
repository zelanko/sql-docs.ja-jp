---
title: setTimestamp (int, java.sql.Timestamp) メソッド |Microsoft ドキュメント
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
- SQLServerPreparedStatement.setTimestamp (int, java.sql.Timestamp)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2f7bb89f-ace7-41cb-b596-5aa8d0dd9e3c
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 57f9d03d51fe4a8b9f6f3bdf5e4c06c34c013092
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32844277"
---
# <a name="settimestamp-method-int-javasqltimestamp"></a>setTimestamp (int, java.sql.Timestamp) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターを、渡されたタイムスタンプ値に設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setTimestamp(int n,  
                               java.sql.Timestamp x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *n*  
  
 **Int**パラメーター数を示すです。  
  
 *x*  
  
 タイムスタンプ オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setTimestamp メソッドは、java.sql.PreparedStatement インターフェイスの setTimestamp メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [setTimestamp メソッド&#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/settimestamp-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
