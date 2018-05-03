---
title: 接続およびデータの取得 |Microsoft ドキュメント
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
ms.assetid: ce43cc20-46a3-42ff-a3fb-75ad1ed10e08
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cd98a0b7954f5b67bedbaa09833b72d8f5914921
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-and-retrieving-data"></a>接続およびデータの取得
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  作業する場合、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]への接続を確立するための 2 つの主要な方法がある、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。 接続 URL における接続のプロパティを設定および DriverManager クラスを返すの getConnection メソッドを呼び出すには、1 つ、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。  
  
> [!NOTE]  
>  JDBC ドライバーでサポートされている接続のプロパティの一覧は、次を参照してください。[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)です。  
  
 2 番目の方法では、setter メソッドを使用して接続プロパティの設定では、 [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)クラス、および呼び出すことで、 [getConnection](../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)を SQLServerConnection を返すメソッドオブジェクト。  
  
 このセクションのトピックに接続できるさまざまな方法を説明する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース、およびそれらのデータを取得するためのさまざまな手法も示しています。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[接続 URL のサンプル](../../connect/jdbc/connection-url-sample.md)|接続 URL を使用してに接続する方法について説明[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]し、SQL ステートメントを使用して、データを取得します。|  
|[データ ソースのサンプル](../../connect/jdbc/data-source-sample.md)|データ ソースを使用して SQL Server に接続し、ストアド プロシージャを使用してデータを取得する方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [サンプル JDBC Driver アプリケーション](../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
  
