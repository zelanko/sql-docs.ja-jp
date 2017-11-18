---
title: "unwrap メソッド (SQLServerConnectionPoolDataSource) |Microsoft ドキュメント"
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
ms.assetid: f5c9b734-2096-4ae4-a284-6b4d1b4a00d4
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8e19a9c15e6bced2f9b0df99e491cdbb0ac8240a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="unwrap-method-sqlserverconnectionpooldatasource"></a>unwrap メソッド (SQLServerConnectionPoolDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  アクセス許可を指定したインターフェイスを実装するオブジェクトを返します、 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-特定のメソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
  
public <T> T unwrap(Class<T> iface)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *iface*  
  
 型のクラス**T**インターフェイスを定義します。  
  
## <a name="return-value"></a>戻り値  
 指定されたインターフェイスを実装するオブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 [Unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverconnectionpooldatasource.md) JDBC 4.0 仕様で導入された java.sql.Wrapper インターフェイスでメソッドが定義されています。  
  
 アプリケーションに固有の JDBC api 拡張機能にアクセスする必要があります、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]です。 Unwrap メソッドは、クラスがベンダー拡張機能を公開する場合のこのオブジェクトを拡張するクラスをパブリックにアンラッピングをサポートします。  
  
 [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)クラスを拡張、 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)クラスです。 このメソッドが呼び出されると、オブジェクトにアンラップ、 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)クラスおよび[SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)クラスです。  
  
 詳細については、次を参照してください。[ラッパーとインターフェイス](../../../connect/jdbc/wrappers-and-interfaces.md)です。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnectionPoolDataSource のメソッド](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-methods.md)   
 [SQLServerConnectionPoolDataSource のメンバー](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-members.md)   
 [SQLServerConnectionPoolDataSource クラス](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
  

