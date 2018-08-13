---
title: パラメーターのメタデータを使用して |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: db2c1957-91c6-4989-a07b-9f8be6d2033a
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 825494c70ea9ed5d36cbf1c16ed4cdedfbfbd87d
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39661734"
---
# <a name="using-parameter-metadata"></a>パラメーターのメタデータの使用

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) または [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) オブジェクトで格納されているパラメーターについてクエリする用途向けに、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] には、[SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md) クラスが実装されています。 このクラスには、単一値の形式で情報を返すフィールドおよびメソッドが多数存在します。

SQLServerParameterMetaData オブジェクトを作成するには、使用することができます、 [getParameterMetaData](../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md) SQLServerPreparedStatement クラスおよび SQLServerCallableStatement クラスのメソッド。

次の例では、開いている接続を[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベース関数に渡される、SQLServerCallableStatement クラスの getParameterMetaData メソッドを使用して、返す SQLServerParameterMetaData オブジェクト、およびさまざまなしSQLServerParameterMetaData オブジェクトのメソッドを使用して、型と、HumanResources.uspUpdateEmployeeHireInfo ストアド プロシージャ内に含まれるパラメーターのモードに関する情報を表示できます。

[!code[JDBC#UsingParamMetaData1](../../connect/jdbc/codesnippet/Java/using-parameter-metadata_1.java)]  

> [!NOTE]  
> 準備されたステートメントを SQLServerParameterMetaData クラスを使用する場合は、いくつかの制限があります。
>
> **SQL Server 向け Microsoft JDBC Driver 6.0 (以上) を使用する場合**: SELECT、DELETE、INSERT、UPDATE にサブクエリや結合が含まれていなければ、SQL Server 2008 または 2008 R2 を使用するとき、JDBC ドライバーはこれらのステートメントをサポートします。

SQL Server 2008 または 2008 R2 を使用するとき、SQLServerParameterMetaData クラスでは、MERGE クエリもサポートされません。 SQL Server 2012 以降のバージョンの場合、複雑なクエリを持つパラメーター メタデータがサポートされます。

暗号化された列のパラメーター メタデータの取得はサポートされていません。 **SQL Server 向け Microsoft JDBC Driver 4.1 または 4.2 を使用する場合**: SELECT、DELETE、INSERT、UPDATE にサブクエリや結合が含まれていなければ、JDBC ドライバーはこれらのステートメントをサポートします。 クエリのマージはも SQLServerParameterMetaData クラスのサポートされません。
