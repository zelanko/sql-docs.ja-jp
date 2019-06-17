---
title: SQLServerXADataSource クラス |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 95fc7b07-2498-4a7e-8f7f-ee0d86b598b4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 5725da0138ecec2e24f93e16af97a1d3c8a67681
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66776031"
---
# <a name="sqlserverxadatasource-class"></a>SQLServerXADataSource クラス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  内部で使用されている [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) オブジェクトのファクトリを表します。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **拡張:** [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
 **実装**: javax.sql.XADataSource  
  
## <a name="syntax"></a>構文  
  
```  
  
public class SQLServerXADataSource  
```  
  
## <a name="remarks"></a>Remarks  
 SQLServerXADataSource インターフェイスを実装するオブジェクトは、通常、JNDI (Java Naming and Directory Interface) を使用するネーム サービスに登録されます。  
  
 SQLServerXADataSource クラスでは、分散 (XA) トランザクションで使用するデータベース接続が提供されます。 SQLServerXADataSource クラスは、物理接続の接続プールもサポートします。 Javax.sql パッケージで定義されている SQLServerXADataSource と SQLServerXAConnection インターフェイスによって実装が[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]します。  
  
 SQLServerXAConnection オブジェクトは、分散トランザクションに参加できるプール接続です。 SQLServerXAConnection が SQLServerPooledConnection インターフェイスを拡張メソッドを追加することで正確には、 [getXAResource](../../../connect/jdbc/reference/getxaresource-method-sqlserverxaconnection.md)します。 このメソッドでは、[SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) オブジェクトが生成されます。トランザクション マネージャーでは、このオブジェクトを使用して、該当する接続で行われる処理を分散トランザクションの他の参加要素と調整できます。 SQLServerPooledConnection インターフェイスを拡張する SQLServerXAConnection オブジェクトは、SQLServerPooledConnection オブジェクトのすべてのメソッドをサポートします。 これらは基になるデータ ソースへの再利用可能な物理的接続であり、JDBC アプリケーションに返される論理接続ハンドルを生成します。  
  
 SQLServerXAConnection オブジェクトは、SQLServerXADataSource オブジェクトによって生成されます。 SQLServerConnectionPoolDataSource オブジェクトと SQLServerXADataSource オブジェクトは、いずれも JDBC アプリケーションに表示されているデータ ソース層の下実装されるため、似ています。 このアーキテクチャでは、アプリケーションに対して透過的な方法で分散トランザクションが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によってサポートされます。 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] 分散トランザクション コーディネーター (DTC) と統合して、真の分散トランザクション サポートが提供されるように、SQLServerXADataSource を構成することができます。  
  
## <a name="see-also"></a>参照  
 [SQLServerXADataSource のメンバー](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [JDBC Driver API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
