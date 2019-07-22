---
title: パラメーターのメタデータを使用する |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: db2c1957-91c6-4989-a07b-9f8be6d2033a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 168a153ecf12acda5adfbae22d13618669c6c2a4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916213"
---
# <a name="using-parameter-metadata"></a>パラメーターのメタデータの使用

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) または [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) オブジェクトで格納されているパラメーターについてクエリする用途向けに、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] には、[SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md) クラスが実装されています。 このクラスには、単一値の形式で情報を返すフィールドおよびメソッドが多数存在します。

SQLServerParameterMetaData オブジェクトを作成するには、SQLServerPreparedStatement クラスと SQLServerCallableStatement クラスの[Getparametermetadata](../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md)メソッドを使用します。

次の例では、 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプルデータベースへの開いている接続を関数に渡し、SQLServerCallableStatement クラスの getparametermetadata メソッドを使用して SQLServerParameterMetaData オブジェクトを返し、その後、さまざまなSQLServerParameterMetaData オブジェクトのメソッドは、Humanresources.employee ストアドプロシージャに含まれるパラメーターの型およびモードに関する情報を表示するために使用されます。

[!code[JDBC#UsingParamMetaData1](../../connect/jdbc/codesnippet/Java/using-parameter-metadata_1.java)]  

> [!NOTE]  
> SQLServerParameterMetaData クラスを準備されたステートメントで使用する場合、いくつかの制限があります。
>
> **SQL Server 向け Microsoft JDBC Driver 6.0 (以上) を使用する場合**: SELECT、DELETE、INSERT、UPDATE にサブクエリや結合が含まれていなければ、SQL Server 2008 または 2008 R2 を使用するとき、JDBC ドライバーはこれらのステートメントをサポートします。

SQL Server 2008 または 2008 R2 を使用するとき、SQLServerParameterMetaData クラスでは、MERGE クエリもサポートされません。 SQL Server 2012 以降のバージョンの場合、複雑なクエリを持つパラメーター メタデータがサポートされます。

暗号化された列のパラメーターメタデータの取得はサポートされていません。 **SQL Server 向け Microsoft JDBC Driver 4.1 または 4.2 を使用する場合**: SELECT、DELETE、INSERT、UPDATE にサブクエリや結合が含まれていなければ、JDBC ドライバーはこれらのステートメントをサポートします。 マージクエリは、SQLServerParameterMetaData クラスでもサポートされていません。
