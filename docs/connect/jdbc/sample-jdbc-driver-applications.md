---
title: JDBC ドライバー アプリケーションのサンプル |Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e136b87c-a138-45d6-8c3e-bcef94b7e483
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9f27838db078539fd82421e23392de79db6166b1
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2018
ms.locfileid: "42786148"
---
# <a name="sample-jdbc-driver-applications"></a>サンプル JDBC Driver アプリケーション

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] サンプル アプリケーションは、JDBC ドライバーのさまざまな機能を示しています。 さらに、JDBC ドライバーを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースで使用するときに参考にできる、適切なプログラミング例も示します。  
  
すべてのサンプル アプリケーションは、ローカル コンピューターでコンパイルおよび実行することができる *.java コード ファイルに含まれ、これらは次の場所の各サブフォルダーに格納されています。  

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples  
```

このセクションのトピックでは、サンプル アプリケーションを構成および実行する方法と、サンプル アプリケーションが示す内容について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
| トピック                                                                                                        | [説明]                                                                                                                                                                                                                                                             |
| ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [接続およびデータの取得](../../connect/jdbc/connecting-and-retrieving-data.md)                       | これらのサンプル アプリケーションは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースへの接続方法を示します。 また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースからデータを取得するさまざまな方法も示します。 |
| [データ型の処理 &#40;JDBC&#41;](../../connect/jdbc/working-with-data-types-jdbc.md)                 | これらのサンプル アプリケーションは、JDBC ドライバーのデータ型のメソッドを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース内のデータを処理する方法を示します。                                                                                           |
| [結果セットの処理](../../connect/jdbc/working-with-result-sets.md)                                   | これらのサンプル アプリケーションは、結果セットを使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに含まれるデータを処理する方法を示します。                                                                                                         |
| [大きなデータの処理](../../connect/jdbc/working-with-large-data.md)                                     | これらのサンプル アプリケーションは、アダプティブ バッファリングを使用して、サーバー カーソルのオーバーヘッドを発生させることなく、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースから大きな値のデータを取得する方法を示します。                                                      |
| [SQL データの検出と分類](../../connect/jdbc/data-discovery-classification-sample.md) | このサンプル アプリケーションはどのように取得するデータの検出と分類の情報に含まれている、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] JDBC ドライバーを使用して結果セット オブジェクトからのデータベース。                                      |
  
## <a name="see-also"></a>参照

[JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  