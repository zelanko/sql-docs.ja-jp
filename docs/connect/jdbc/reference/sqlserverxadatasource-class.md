---
title: "SQLServerXADataSource クラス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95fc7b07-2498-4a7e-8f7f-ee0d86b598b4
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 10e470658b2f0b3954d97bc2632ca25c53745d2f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverxadatasource-class"></a>SQLServerXADataSource クラス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  ファクトリを表します[SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)内部的に使用されるオブジェクト。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **拡張:** [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
 **実装:** javax.sql.XADataSource  
  
## <a name="syntax"></a>構文  
  
```  
  
public class SQLServerXADataSource  
```  
  
## <a name="remarks"></a>解説  
 SQLServerXADataSource インターフェイスを実装するオブジェクトは、通常、名前付けサービスを Java Naming and Directory Interface (JNDI) を使用して登録します。  
  
 SQLServerXADataSource クラスは、分散 (XA) トランザクションで使用されるデータベース接続を提供します。 SQLServerXADataSource クラスは、物理接続の接続プールもサポートします。 Javax.sql パッケージで定義されている SQLServerXADataSource と SQLServerXAConnection インターフェイスはによって実装される[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。  
  
 SQLServerXAConnection オブジェクトは、分散トランザクションに参加できるプール接続です。 メソッドを追加することによって、SQLServerXAConnection が SQLServerPooledConnection インターフェイスを拡張する具体的には、 [getXAResource](../../../connect/jdbc/reference/getxaresource-method-sqlserverxaconnection.md)です。 このメソッドを生成、 [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)トランザクション マネージャーによって、分散トランザクションに他の参加者とは、この接続で行われる作業を調整するために使用するオブジェクト。 SQLServerPooledConnection インターフェイスを拡張するため、SQLServerXAConnection オブジェクトは、SQLServerPooledConnection オブジェクトのすべてのメソッドをサポートします。 これらは基になるデータ ソースへの再利用可能な物理的接続であり、JDBC アプリケーションに返される論理接続ハンドルを生成します。  
  
 SQLServerXAConnection オブジェクトは、SQLServerXADataSource オブジェクトによって生成されます。 SQLServerConnectionPoolDataSource オブジェクトおよび SQLServerXADataSource オブジェクトは、いずれも JDBC アプリケーションに表示されているデータ ソース層の下実装はため似ています。 このアーキテクチャにより[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]アプリケーションに透過的な方法で分散トランザクションをサポートします。 SQLServerXADataSource と統合するように構成できる[!INCLUDE[msCoName](../../../includes/msconame_md.md)]する場合は true、分散トランザクション コーディネーター (DTC) トランザクション処理を分散します。  
  
## <a name="see-also"></a>参照  
 [SQLServerXADataSource のメンバー](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [JDBC ドライバー API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  

