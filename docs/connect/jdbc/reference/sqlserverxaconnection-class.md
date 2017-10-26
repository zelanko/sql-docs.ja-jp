---
title: "SQLServerXAConnection クラス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ecb4bf1-b8d1-47cf-9cb1-7a18acc11ce2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f885d32d2887a9db7c7159025713616c560437c9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverxaconnection-class"></a>SQLServerXAConnection クラス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  分散 (XA) トランザクションに参加できる JDBC 接続を表します。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **拡張:** [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
 **実装:** javax.sql.XAConnection  
  
## <a name="syntax"></a>構文  
  
```  
  
public class SQLServerXAConnection  
```  
  
## <a name="remarks"></a>解説  
 SQLServerXAConnection オブジェクトは、の分散トランザクションに参加させることができます、 [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)オブジェクト。 中間層サーバーの一部では通常、トランザクション マネージャーは、SQLServerXAResource オブジェクトを通じて SQLServerXAConnection オブジェクトを管理します。  
  
> [!NOTE]  
>  通常、アプリケーション プログラマがこのインターフェイスを直接使用することはありません。 このインターフェイスは主に、中間層サーバーで動作しているトランザクション マネージャーによって使用されます。  
  
## <a name="see-also"></a>参照  
 [SQLServerXAConnection のメンバー](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [JDBC ドライバー API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  

