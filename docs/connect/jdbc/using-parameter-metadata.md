---
title: パラメーターのメタデータの使用 | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: db2c1957-91c6-4989-a07b-9f8be6d2033a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 80ff8cebcc4141e8363c25f83821cb4924e6c46a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "69026077"
---
# <a name="using-parameter-metadata"></a>パラメーターのメタデータの使用

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) または [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) オブジェクトで格納されているパラメーターについてクエリする用途向けに、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] には、[SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md) クラスが実装されています。 このクラスには、単一値の形式で情報を返すフィールドおよびメソッドが多数存在します。

SQLServerParameterMetaData オブジェクトを作成するには、SQLServerPreparedStatement クラスと SQLServerCallableStatement クラスの [getParameterMetaData](../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md) メソッドを使用します。

次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] サンプル データベースへのオープン接続が関数に渡され、SQLServerCallableStatement クラスの getParameterMetaData メソッドを使用して SQLServerParameterMetaData オブジェクトが返されます。次に、SQLServerParameterMetaData オブジェクトのさまざまなメソッドが使用され、HumanResources.uspUpdateEmployeeHireInfo ストアド プロシージャ内に含まれているパラメーターの型とモードに関する情報が表示されます。

[!code[JDBC#UsingParamMetaData1](../../connect/jdbc/codesnippet/Java/using-parameter-metadata_1.java)]  

> [!NOTE]  
> 準備されたステートメントで SQLServerParameterMetaData クラスを使用する場合は、いくつかの制限があります。
>
> **SQL Server 向け Microsoft JDBC Driver 6.0 (以上) を使用する場合**: SELECT、DELETE、INSERT、UPDATE にサブクエリや結合が含まれていなければ、SQL Server 2008 または 2008 R2 を使用するとき、JDBC ドライバーはこれらのステートメントをサポートします。

SQL Server 2008 または 2008 R2 を使用するとき、SQLServerParameterMetaData クラスでは、MERGE クエリもサポートされません。 SQL Server 2012 以降のバージョンの場合、複雑なクエリを持つパラメーター メタデータがサポートされます。

暗号化された列に対するパラメーターのメタデータの取得はサポートされていません。 **SQL Server 向け Microsoft JDBC Driver 4.1 または 4.2 を使用する場合**: SELECT、DELETE、INSERT、UPDATE にサブクエリや結合が含まれていなければ、JDBC ドライバーはこれらのステートメントをサポートします。 SQLServerParameterMetaData クラスでは、MERGE クエリもサポートされません。
