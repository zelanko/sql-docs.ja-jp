---
title: setSavepoint () メソッド |Microsoft ドキュメント
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
- SQLServerConnection.setSavepoint ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 11013055-4fd3-45a9-b2da-28b2908dad52
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6777713e555a2ff0da1ca673eb32412d2c99dcfc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32844387"
---
# <a name="setsavepoint-method-"></a>setSavepoint () メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  現在のトランザクションで、名前のないセーブポイントを作成し、新しい返します[SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md)を表すオブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Savepoint setSavepoint()  
```  
  
## <a name="return-value"></a>戻り値  
 セーブポイント オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この setSavePoint メソッドは、java.sql.Connection インターフェイスの setSavePoint メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [setSavepoint メソッド&#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)   
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
