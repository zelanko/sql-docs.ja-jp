---
title: "データ型 (JDBC) の使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b39f44d0-3710-4bc6-880c-35bd8c10a734
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e21871b7baaf79f2fd9bcc8185abe54ce699b0f1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="working-with-data-types-jdbc"></a>データ型の処理 (JDBC)
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  主な機能、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 、Java 開発者に含まれるデータにアクセスできるようにする[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。 これを実現する、JDBC ドライバーは間で変換を仲介[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型と Java 言語型およびオブジェクト。  
  
> [!NOTE]  
>  詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]し、それらの相違点と Java 言語のデータ型に変換する方法を含む JDBC ドライバーのデータ型を参照してください[JDBC ドライバーのデータ型について](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)です。  
  
 SQL Server データ型を使用するために、JDBC ドライバーには get\<型 > 設定と\<型 > のメソッド、 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)と[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md)クラス、およびその提供 get\<型 > および更新\<型 > のメソッド、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)クラス。 使用するメソッドは、処理するデータの型と、結果セットまたはクエリを使用するかどうかによって決まります。  
  
 このセクションのトピックでは、JDBC ドライバーのデータ型を使用してアクセスする方法を説明[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Java アプリケーション内のデータ。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[基本データ型のサンプル](../../connect/jdbc/basic-data-types-sample.md)|結果セットの getter メソッドを使用して基本的なを取得する方法について説明します[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データ型の値、および結果セットの update メソッドを使用して、それらの値を更新する方法です。|  
|[SQLXML データ型のサンプル](../../connect/jdbc/sqlxml-data-type-sample.md)|リレーショナル データベースに XML データを格納する方法、データベースから XML データを取得する方法で XML データを解析する方法を説明、 **SQLXML** Java データ型。|  
  
## <a name="see-also"></a>参照  
 [サンプル JDBC Driver アプリケーション](../../connect/jdbc/sample-jdbc-driver-applications.md)  
  
  
