---
title: supportsTransactionIsolationLevel メソッド |Microsoft ドキュメント
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
- SQLServerDatabaseMetaData.supportsTransactionIsolationLevel
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b716ed6c-6ec3-47a7-8e6d-16cbf2469d6d
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 11f676b7f390bee7f67795d7d19bcce26616142e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="supportstransactionisolationlevel-method-sqlserverdatabasemetadata"></a>supportsTransactionIsolationLevel メソッド (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースが渡されたトランザクションの分離レベルをサポートするかどうかを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean supportsTransactionIsolationLevel(int level)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *レベル*  
  
 **Int**トランザクション分離レベルを示すです。  
  
## <a name="return-value"></a>戻り値  
 **true**サポートされている場合。 それ以外の場合は、 **false**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この supportsTransactionIsolationLevel メソッドは、java.sql.DatabaseMetaData インターフェイスの supportsTransactionIsolationLevel メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerDatabaseMetaData のメソッド](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData のメンバー](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData クラス](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
