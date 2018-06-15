---
title: ソースのプロパティのデータを設定 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f3363d05-07fc-4bf8-ae5e-2a7a968808ad
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 13a305b676d43a13ae731bcc98dd3f517a5bf733
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32850387"
---
# <a name="setting-the-data-source-properties"></a>データ ソースのプロパティの設定」を参照してください。
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  データ ソースは、Java Platform, Enterprise Edition (Java EE) 環境で JDBC 接続を作成するために推奨される機構です。 データ ソースは、接続、プールされた接続、および分散接続を提供します。このとき、Java コードに接続プロパティをハード コーディングする必要がありません。 すべて[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]データ ソースを設定したり、適切な setter メソッドと getter メソッドをそれぞれ使用して、任意のプロパティの値を取得します。  
  
 アプリケーション サーバーやサーブレット/JSP エンジンなどの Java EE 製品では、通常、データベース アクセス用にデータ ソースを構成できます。 任意のプロパティに一覧表示、[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)トピックは、任意の場所の構成を入力できる場合、プロパティをプロパティとして指定することができます = 値のペア。  
  
 詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、データ ソースを参照してください、 [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)クラスです。 SQLServerDataSource クラスを使用して接続を確立する方法の例については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースを参照してください[データ ソースのサンプル](../../connect/jdbc/data-source-sample.md)です。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーによる SQL Server への接続](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
