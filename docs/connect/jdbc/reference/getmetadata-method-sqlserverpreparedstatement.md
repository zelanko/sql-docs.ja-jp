---
title: getMetaData メソッド (SQLServerPreparedStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.getMetaData
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5ed49a53-ed61-4e95-ad67-45957aaabb6a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bbc0a0493498f3d216c9e1395f651d8afec70711
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67981865"
---
# <a name="getmetadata-method-sqlserverpreparedstatement"></a>getMetaData メソッド (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerResultSetMetaData Class](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) オブジェクトを取得します。このオブジェクトには、[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトの実行時に返される [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) オブジェクトの列に関する情報が含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final java.sql.ResultSetMetaData getMetaData()  
```  
  
## <a name="return-value"></a>戻り値  
 ResultSetMetaData オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この getMetaData メソッドは、java.sql.PreparedStatement インターフェイスの getMetaData メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
