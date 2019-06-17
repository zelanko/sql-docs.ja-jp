---
title: setSavepoint () メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setSavepoint ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 11013055-4fd3-45a9-b2da-28b2908dad52
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: bf2c9920545d4d17bb8df6979410d849c125e20c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796743"
---
# <a name="setsavepoint-method-"></a>setSavepoint () メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  名前を割り当てられていないセーブポイントを現在のトランザクションに作成し、そのセーブポイントを表す新しい [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) オブジェクトを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.sql.Savepoint setSavepoint()  
```  
  
## <a name="return-value"></a>戻り値  
 セーブポイントのオブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この setSavePoint メソッドは、java.sql.Connection インターフェイスの setSavePoint メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [setSavepoint メソッド &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)   
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
