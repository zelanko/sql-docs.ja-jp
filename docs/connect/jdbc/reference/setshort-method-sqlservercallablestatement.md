---
title: setShort メソッド (SQLServerCallableStatement) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.setShort
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d7031a89-e964-4ffd-87b7-63825799435d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 33d39d7e0242ff7913fd13858cd35fc81ea6858c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47662240"
---
# <a name="setshort-method-sqlservercallablestatement"></a>setShort メソッド (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたパラメーターを、渡された java 値に設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setShort(java.lang.String sCol,  
                     short s)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sCol*  
  
 パラメーターの名前を含む**文字列**です。  
  
 *s*  
  
 A**短い**値。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この setObject メソッドは、java.sql.CallableStatement インターフェイスの setObject メソッドで指定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
