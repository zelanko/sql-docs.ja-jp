---
title: "unwrap メソッド (SQLServerStatement) |Microsoft ドキュメント"
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
ms.assetid: ce680176-ef04-4e44-bb6c-ec50bd06e7e6
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: dbda74967315c5d918a1810ff9221a5c86325078
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="unwrap-method-sqlserverstatement"></a>unwrap メソッド (SQLServerStatement)
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
 [Unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverstatement.md) JDBC 4.0 仕様で導入された java.sql.Wrapper インターフェイスでメソッドが定義されています。  
  
 アプリケーションに固有の JDBC api 拡張機能にアクセスする必要があります、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]です。 Unwrap メソッドは、クラスがベンダー拡張機能を公開する場合のこのオブジェクトを拡張するクラスをパブリックにアンラッピングをサポートします。  
  
 このメソッドが呼び出されると、オブジェクトにアンラップ、 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)クラスです。  
  
 コード例を参照してください[大規模なデータの更新のサンプル](../../../connect/jdbc/updating-large-data-sample.md)、または[unwrap メソッド & #40 です。SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md).  
  
 詳細については、次を参照してください。[ラッパーとインターフェイス](../../../connect/jdbc/wrappers-and-interfaces.md)です。  
  
## <a name="see-also"></a>参照  
 [isWrapperFor メソッドと #40 です。SQLServerStatement &#41;](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverstatement.md)   
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

