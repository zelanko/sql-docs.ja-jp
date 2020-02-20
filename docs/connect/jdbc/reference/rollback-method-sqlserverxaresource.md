---
title: rollback メソッド (SQLServerXAResource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXAResource.rollback
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 93d9d7e6-54b6-4d86-8f8c-386c6057e85e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4245dc4314d955aefc3538a38dcd2192403fed9a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67975726"
---
# <a name="rollback-method-sqlserverxaresource"></a>rollback メソッド (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  トランザクション ブランチのために実行した処理をロールバックするように、リソース マネージャーに要求します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void rollback(javax.transaction.xa.Xid xid)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *xid*  
  
 Xid オブジェクト。  
  
## <a name="exceptions"></a>例外  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>解説  
 この rollback メソッドは、javax.transaction.xa.XAResource インターフェイスの rollback メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [SQLServerXAResource のメソッド](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource のメンバー](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource クラス](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
