---
title: rollback メソッド (java.sql.Savepoint) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.rollback (java.sql.Savepoint)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d5dbd9ef-194f-4130-bfcc-7901a4fa8ded
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2e1ac014ddeee1d3763dc3cebe720751c4c1ec94
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80903887"
---
# <a name="rollback-method-javasqlsavepoint"></a>rollback (java.sql.Savepoint) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) オブジェクトが設定された後で行われた変更を、すべて元に戻します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void rollback(java.sql.Savepoint s)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *s*  
  
 ロールバック先の SavePoint オブジェクト。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この rollBack メソッドは、java.sql.Connection インターフェイスの rollBack メソッドによって指定されます。  
  
 このメソッドは、自動コミット モードが無効になっている場合にのみ使用してください。  
  
## <a name="see-also"></a>参照  
 [rollback メソッド &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md)   
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
