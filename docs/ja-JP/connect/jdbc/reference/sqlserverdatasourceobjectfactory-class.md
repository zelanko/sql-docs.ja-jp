---
title: SQLServerDataSourceObjectFactory クラス |Microsoft ドキュメント
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
ms.topic: conceptual
ms.assetid: b616632b-5987-470d-b36c-b22fa9213145
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3b8d13a403cff4d6b3f955bf560ef17f98eae36d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlserverdatasourceobjectfactory-class"></a>SQLServerDataSourceObjectFactory クラス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  JNDI (Java Naming and Directory Interface) からのデータ ソースを生成するオブジェクト ファクトリを表します。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **拡張:** java.lang.Object  
  
 **実装:** javax.naming.spi.ObjectFactory  
  
## <a name="syntax"></a>構文  
  
```  
  
public class SQLServerDataSourceObjectFactory  
```  
  
## <a name="remarks"></a>解説  
 このクラスはすべてのデータ ソース クラスに継承されます。 Referenceable インターフェイスのサポートの一部として[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]ObjectFactory を実装するこのクラスを公開します。 Java アプリケーション サーバーは、データ ソース クラスの getReference を呼び出すし、これのクラス ファクトリとして内部的にクラス名を使用して参照オブジェクトが作成されます。  
  
 Java アプリケーション サーバーは、参照されたオブジェクトを逆参照するのには、SQLServerDataSourceObjectFactory オブジェクトと呼び出しのインスタンスが作成されます、 [getObjectInstance](../../../connect/jdbc/reference/getobjectinstance-method-sqlserverdatasourceobjectfactory.md)参照は、オブジェクトに渡して、メソッドデータ ソースのインスタンスを取得します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSourceObjectFactory のメンバー](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [JDBC ドライバー API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
