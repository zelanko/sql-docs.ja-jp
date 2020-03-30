---
title: unwrap メソッド (SQLServerPreparedStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8e3ec950-3ac1-4c28-9e97-ddce3bd46578
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 81e533e32504df219155259e9639c83c3be4c647
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "67985592"
---
# <a name="unwrap-method-sqlserverpreparedstatement"></a>unwrap メソッド (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定されたインターフェイスを実装するオブジェクトを返します。このメソッドから返されたオブジェクトを使用することで、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 固有のメソッドにアクセスできます。  
  
## <a name="syntax"></a>構文  
  
```  
  
public <T> T unwrap(Class<T> iface)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *iface*  
  
 インターフェイスを定義する **T** 型のクラスです。  
  
## <a name="return-value"></a>戻り値  
 指定されたインターフェイスを実装するオブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 [unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverpreparedstatement.md) メソッドは、JDBC 4.0 仕様で導入された java.sql.Wrapper インターフェイスで定義されています。  
  
 アプリケーションは [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] に固有の JDBC API 拡張機能にアクセスする必要がある場合があります。 unwrap メソッドは、クラスがベンダー拡張を公開する場合、このオブジェクトが拡張するパブリック クラスへのアンラッピングをサポートします。  
  
 このメソッドが呼び出されると、オブジェクトは [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) クラスおよび [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) クラスにアンラップされます。  
  
 コードの例については、「[unwrap メソッド (SQLServerCallableStatement)](../../../connect/jdbc/reference/unwrap-method-sqlservercallablestatement.md)」を参照してください。  
  
 詳細については、「[ラッパーとインターフェイス](../../../connect/jdbc/wrappers-and-interfaces.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [isWrapperFor メソッド &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
