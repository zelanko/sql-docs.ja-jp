---
title: XML データのサポート |Microsoft ドキュメント
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
ms.assetid: 32b7217e-1f0c-473d-9a45-176daa81584e
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d23e602f9e1323f96bc350d2501dccf6e06b03ca
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="supporting-xml-data"></a>XML データのサポート
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 提供、 **xml**データ型を XML ドキュメントを格納して、フラグメント、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。 **Xml**データ型は、組み込みのデータ型で[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]などの他の組み込み型のようないくつかの方法であると**int**と**varchar**です。 他の組み込み型と同様に使用することができます、 **xml**データ型として: 変数の型、パラメーターの型、関数の戻り値の型、または列が入力またはテーブルを作成する場合に[!INCLUDE[tsql](../../includes/tsql_md.md)]CAST や CONVERT 関数。 JDBC ドライバーで、 **xml**データ型は、文字列、バイト配列、ストリーム、CLOB、BLOB、または SQLXML オブジェクトとしてマップすることができます。 文字列が既定のマッピングです。  
  
 この JDBC ドライバーがサポートする JDBC 4.0 API には、SQLXML インターフェイスが導入されています。 SQLXML インターフェイスには、XML データを操作するための各種のメソッドが定義されています。 **SQLXML** JDBC 4.0 のデータ型は、マップ先、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **xml**データ型。 したがって、アプリケーション内で SQLXML データ型を使用する場合は、sqljdbc4.jar ファイルをインクルードするためのクラスパスを設定する必要があります。 アプリケーションから sqljdbc3.jar を使用して SQLXML オブジェクトやそのメソッドにアクセスしようとすると、例外がスローされます。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] データベース列に格納する前に、XML データを必ず検証します。 アプリケーションを使用して**SQLXML**データ型の JDBC ドライバーにマップするため、 **xml**データを自動的に入力します。 **SQLXML**サポートは sqljdbc4.jar にします。 参照してください[JDBC Driver のシステム要件](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)によってサポートされる JRE バージョンの一覧については、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]です。  
  
 このセクションのトピックでは、SQLXML インターフェイスおよびをプログラミングする方法について説明、 **SQLXML** JDBC API のメソッドを使用して、データ型。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[SQLXML インターフェイス](../../connect/jdbc/sqlxml-interface.md)|SQLXML のインターフェイスとそのメソッドについて説明します。|  
|[SQLXML でのプログラミング](../../connect/jdbc/programming-with-sqlxml.md)|使用する方法について説明します、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] API のメソッドを格納およびリレーショナル データベースから XML データの取得、 **SQLXML** Java データ型。 SQLXML オブジェクトの型についての情報や、SQLXML オブジェクトを使用するうえでの重要なガイドラインおよび制限事項の一覧も掲載されています。|  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーのデータ型について](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
