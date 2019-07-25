---
title: データベースメタデータの使用 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8b048371-e912-4ed1-afd7-436978f48888
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fbe290c558dd8c64605bad0a977657904582c696
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916265"
---
# <a name="using-database-metadata"></a>データベースのメタデータの使用

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

データベースのサポート内容に関する情報をクエリする用途向けに、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] には、[SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) クラスが実装されています。 このクラスには、単一値形式または結果セットとして情報を返すメソッドが多数存在します。

SQLServerDatabaseMetaData オブジェクトを作成するには、[SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) クラスの [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md) メソッドを使用して接続先のデータベースに関する情報を取得します。

次の例では、 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプルデータベースに対して開いている接続を関数に渡し、SQLServerConnection クラスの getmetadata メソッドを使用して SQLServerDatabaseMetadata オブジェクトを返します。その後、SQLServerDatabaseMetaData オブジェクトは、ドライバー、ドライバーのバージョン、データベース名、およびデータベースのバージョンに関する情報を表示するために使用されます。

[!code[JDBC#UsingDBMetaData1](../../connect/jdbc/codesnippet/Java/using-database-metadata_1.java)]

## <a name="see-also"></a>参照

[JDBC ドライバーによるメタデータの処理](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)
