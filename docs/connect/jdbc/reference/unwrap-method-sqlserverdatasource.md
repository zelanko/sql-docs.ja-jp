---
title: unwrap メソッド (SQLServerDataSource) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb8abe29-f3ec-4752-a590-1d5dc3e48f08
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e12aef2b57384fa89eb3db28a3d0c16a124bfad6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="unwrap-method-sqlserverdatasource"></a>unwrap メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  アクセス許可を指定したインターフェイスを実装するオブジェクトを返します、 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-特定のメソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
  
public <T> T unwrap(Class<T> iface)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *iface*  
  
 インターフェイスを定義する T 型のクラスです。  
  
## <a name="return-value"></a>戻り値  
 指定されたインターフェイスを実装するオブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 [Unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md) JDBC 4.0 仕様で導入された java.sql.Wrapper インターフェイスでメソッドが定義されています。  
  
 アプリケーションに固有の JDBC api 拡張機能にアクセスする必要があります、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]です。 Unwrap メソッドは、クラスがベンダー拡張機能を公開する場合に、このオブジェクトが拡張するパブリック クラスへのアンラッピングをサポートします。  
  
 このメソッドが呼び出されると、オブジェクトにアンラップ、 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)クラスです。  
  
 詳細については、次を参照してください。[ラッパーとインターフェイス](../../../connect/jdbc/wrappers-and-interfaces.md)です。  
  
## <a name="see-also"></a>参照  
 [isWrapperFor メソッド&#40;SQLServerDataSource&#41;](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverdatasource.md)   
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
