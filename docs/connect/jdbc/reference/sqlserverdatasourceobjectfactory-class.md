---
title: SQLServerDataSourceObjectFactory クラス |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b616632b-5987-470d-b36c-b22fa9213145
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ecec8f58587d6a57468f8078e1f680675bede77
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38046850"
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
  
## <a name="remarks"></a>Remarks  
 このクラスはすべてのデータ ソース クラスに継承されます。 Referenceable インターフェイスのサポートの一部として、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] では、ObjectFactory を実装するこのクラスが公開されています。 Java アプリケーション サーバーはデータ ソース クラスで getReference を呼び出し、それによって、内部的にクラス名をクラス ファクトリとして使用する Reference オブジェクトが作成されます。  
  
 SQLServerDataSourceObjectFactory のオブジェクトと呼び出しのインスタンスを作成、参照オブジェクトを逆参照する場合、Java アプリケーション サーバー、 [getObjectInstance](../../../connect/jdbc/reference/getobjectinstance-method-sqlserverdatasourceobjectfactory.md)参照オブジェクトを渡してメソッドデータ ソースのインスタンスを取得します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSourceObjectFactory のメンバー](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [JDBC Driver API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
