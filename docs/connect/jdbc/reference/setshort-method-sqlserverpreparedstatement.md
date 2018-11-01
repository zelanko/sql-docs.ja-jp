---
title: setShort メソッド (SQLServerPreparedStatement) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setShort
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6a9171a4-3e44-44ea-a453-23f57e5320e9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3532554a9ae4b03e37bd455fe35a6fed58768bba
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47621670"
---
# <a name="setshort-method-sqlserverpreparedstatement"></a>setShort メソッド (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターを、渡された **short** 値に設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final void setShort(int index,  
                           short x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *index*  
  
 パラメーターの番号を示す **int** です。  
  
 *x*  
  
 A**短い**値。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この setShort メソッドは、java.sql.PreparedStatement インターフェイスの setShort メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
