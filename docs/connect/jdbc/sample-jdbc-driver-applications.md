---
title: サンプル JDBC ドライバー アプリケーション
description: JDBC Driver for SQL Server のサンプル アプリケーションには、さまざまな機能と、JDBC ドライバーを使用するときに採用できる優れたプログラミング手法が示されています。
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e136b87c-a138-45d6-8c3e-bcef94b7e483
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e55eb9d0e710ba41089dcb014e9e626343ea4e91
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2020
ms.locfileid: "81634261"
---
# <a name="sample-jdbc-driver-applications"></a>サンプル JDBC ドライバー アプリケーション

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] サンプル アプリケーションは、JDBC ドライバーのさまざまな機能を示しています。 さらに、JDBC ドライバーを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースで使用するときに参考にできる、適切なプログラミング例も示します。  
  
すべてのサンプル アプリケーションは、ローカル コンピューターでコンパイルおよび実行することができる *.java コード ファイルに含まれ、これらは次の場所の各サブフォルダーに格納されています。  

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples  
```

このセクションのトピックでは、サンプル アプリケーションを構成および実行する方法と、サンプル アプリケーションが示す内容について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
| トピック                                                                                                        | 説明                                                                                                                                                                                                                                                             |
| ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [接続およびデータの取得](connecting-and-retrieving-data.md)                       | これらのサンプル アプリケーションは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースへの接続方法を示します。 また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースからデータを取得するさまざまな方法も示します。 |
| [データ型の処理 &#40;JDBC&#41;](working-with-data-types-jdbc.md)                 | これらのサンプル アプリケーションは、JDBC ドライバーのデータ型のメソッドを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース内のデータを処理する方法を示します。                                                                                           |
| [結果セットの処理](../../connect/jdbc/working-with-result-sets.md)                                   | これらのサンプル アプリケーションは、結果セットを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに含まれるデータを処理する方法を示します。                                                                                                         |
| [大きなデータの処理](../../connect/jdbc/working-with-large-data.md)                                     | これらのサンプル アプリケーションは、アダプティブ バッファリングを使用して、サーバー カーソルのオーバーヘッドを発生させることなく、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースから大きな値のデータを取得する方法を示します。                                                      |
| [SQL データの検出と分類](../../connect/jdbc/data-discovery-classification-sample.md) | このサンプル アプリケーションでは、JDBC ドライバーを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに格納されているデータの検出と分類の情報を ResultSet オブジェクトから取得する方法を示します。                                      |
  
## <a name="see-also"></a>関連項目

[JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
