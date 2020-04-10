---
title: データ型の処理 (JDBC) | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b39f44d0-3710-4bc6-880c-35bd8c10a734
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d05200ff0c634ea327e58e5288ff8e99c0ec9418
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922560"
---
# <a name="working-with-data-types-jdbc"></a>データ型の処理 (JDBC)

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] の主な機能は、Java 開発者が、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに含まれたデータにアクセスできるようにすることです。 これを可能にするために、JDBC ドライバーは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型と Java 言語の型やオブジェクトとの間の変換を仲介します。  
  
> [!NOTE]  
> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] および JDBC ドライバーのデータ型について、その相違点や Java 言語のデータ型への変換方法など、詳細については、「[JDBC ドライバーのデータ型について](../../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)」を参照してください。  
  
SQL Server のデータ型を処理するために、JDBC ドライバーには、\<SQLServerPreparedStatement\< クラスおよび [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) クラスに get[Type> メソッドおよび set](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)Type> メソッドがあり、\<SQLServerResultSet\< クラスに get[Type> メソッドおよび update](../../../connect/jdbc/reference/sqlserverresultset-class.md)Type> メソッドがあります。 使用するメソッドは、処理するデータの型と、結果セットまたはクエリを使用するかどうかによって決まります。  
  
このセクションのトピックでは、JDBC ドライバーのデータ型を使用して Java アプリケーションの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データにアクセスする方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
| トピック                                                                         | 説明                                                                                                                                                                                                                                                  |
| ----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [基本データ型のサンプル](../../../connect/jdbc/code-samples/basic-data-types-sample.md)   | 結果セットの getter メソッドを使用して基本的な [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型の値を取得する方法と、結果セットの update メソッドを使用してそれらの値を更新する方法を示しています。                                             |
| [SQLXML データ型のサンプル](../../../connect/jdbc/code-samples/sqlxml-data-type-sample.md)   | XML データのリレーショナル データベースへの格納、データベースからの XML データの取得、および、XML データの解析を、**SQLXML** Java データ型を使用して行う方法を示しています。                                                                                   |
| [空間データ型のサンプル](../../../connect/jdbc/code-samples/spatial-data-types-sample.md) | 空間データ型を SQL Server に格納する方法と、これらの型を SQL Server から取得する方法について説明します。 また、これらのデータ型の Java 参照を管理するために、ドライバーの新しく定義されたクラスである **Geometry** と**Geography** を使用する方法についても説明します。 |
  
## <a name="see-also"></a>参照

[サンプル JDBC ドライバー アプリケーション](../../../connect/jdbc/code-samples/sample-jdbc-driver-applications.md)  
