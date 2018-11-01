---
title: setFetchSize メソッド (SQLServerStatement) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setFetchSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 760e555e-9667-4b40-b0ba-778026ff2923
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ed9b715748afbbde4dc58fcd4df9c96b4011d944
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47605630"
---
# <a name="setfetchsize-method-sqlserverstatement"></a>setFetchSize メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  さらに行が必要な場合にデータベースからフェッチする必要がある行数について、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] にヒントを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setFetchSize(int rows)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *rows*  
  
 フェッチする行数を示す **int** です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この setFetchSize メソッドは、java.sql.Statement インターフェイスの setFetchSize メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
