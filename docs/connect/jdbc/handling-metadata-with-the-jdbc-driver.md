---
title: JDBC ドライバーによるメタデータの処理 |Microsoft ドキュメント
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
ms.assetid: 5cfb35d4-ddcd-40a2-8091-f29cddc32552
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 947a72d4aa0339b0ec47bc82054fcc34ceeedc74
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="handling-metadata-with-the-jdbc-driver"></a>JDBC ドライバーによるメタデータの処理
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]内のメタデータを操作するために使用する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]さまざまな方法でデータベース。 JDBC ドライバーでは、データベースのメタデータを、結果セットまたはパラメーターとして取得することができます。  
  
 JDBC ドライバーからメタデータを取得するための 3 つのクラスの提供、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。  
  
-   [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)、現在接続しているデータベースに関する情報を返すために使用します。  
  
-   [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)、結果セットに関する情報を返すために使用します。  
  
-   [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md)、準備された、呼び出し可能ステートメントのパラメーターに関する情報を返すために使用します。  
  
 このセクションのトピックでは、これらの 3 つのメタデータ クラスを内のメタデータを使用する使用方法について説明、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。  
  
> [!NOTE]  
>  このセクションで説明されているメタデータ メソッドは、通常はアプリケーションのパフォーマンスに対する負荷が大きいため、使用する際は注意が必要です。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[データベースのメタデータの使用](../../connect/jdbc/using-database-metadata.md)|現在接続しているデータベースのメタデータ情報を取得する方法を説明します。|  
|[結果セットのメタデータの使用](../../connect/jdbc/using-result-set-metadata.md)|現在の結果セットのメタデータ情報を取得する方法を説明します。|  
|[パラメーターのメタデータの使用](../../connect/jdbc/using-parameter-metadata.md)|準備されたステートメントおよび呼び出し可能なステートメントのパラメーターのメタデータ情報を取得する方法を説明します。|  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
