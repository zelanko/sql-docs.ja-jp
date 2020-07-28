---
title: 接続およびデータの取得
description: Microsoft JDBC Driver for SQL Server とこれらのコード サンプルを使用して、SQL データベースに接続してデータを取得する方法について説明します。
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ce43cc20-46a3-42ff-a3fb-75ad1ed10e08
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 92565d42605b67f61d3ab5e3842e3fb9f110b626
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86922888"
---
# <a name="connecting-and-retrieving-data"></a>接続およびデータの取得

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] を使用する場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースへの接続を確立する 2 つの主な方法があります。 1 つは、接続 URL の接続プロパティを設定してから、DriverManager クラスの getConnection メソッドが呼び出され、[SQLServerConnection](reference/sqlserverconnection-class.md) オブジェクトが返される方法です。

> [!NOTE]
> JDBC ドライバーでサポートされる接続プロパティの一覧については、「[接続プロパティの設定](setting-the-connection-properties.md)」を参照してください。

2 つ目の方法では、[SQLServerDataSource](reference/sqlserverdatasource-class.md) クラスの setter メソッドを使用して接続プロパティを設定してから、[getConnection](reference/getconnection-method-sqlserverdatasource.md) メソッドが呼び出され、SQLServerConnection オブジェクトが返されます。

このセクションのトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続するさまざまな方法について説明し、データを取得するさまざまな手法も示します。

## <a name="in-this-section"></a>このセクションの内容

| トピック                                             | 説明                                                                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [接続 URL のサンプル](connection-url-sample.md) | 接続 URL を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続してから、SQL ステートメントを使用してデータを取得する方法について説明します。 |
| [データ ソースのサンプル](data-source-sample.md)       | データ ソースを使用して SQL Server に接続し、ストアド プロシージャを使用してデータを取得する方法について説明します。                                                 |

## <a name="see-also"></a>関連項目

[サンプル JDBC ドライバー アプリケーション](sample-jdbc-driver-applications.md)
