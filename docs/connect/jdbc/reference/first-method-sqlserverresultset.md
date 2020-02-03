---
title: first メソッド (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.first
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 67ed9447-7b10-4c87-98e7-f4c2e2470b3a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 98f35916270d7cb7026e994cb11d564d70739c7e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67954554"
---
# <a name="first-method-sqlserverresultset"></a>first メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトの先頭行にカーソルを移動します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean first()  
```  
  
## <a name="return-value"></a>戻り値  
 カーソルが先頭行に移動した場合は、**true** です。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この first メソッドは、java.sql.ResultSet インターフェイスの first メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
