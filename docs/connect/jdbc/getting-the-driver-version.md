---
title: "ドライバー バージョンの取得 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e241d72-16da-4ada-ac67-e6308394108f
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b7578539a178e76796018d2da307381318414cb0
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2018
---
# <a name="getting-the-driver-version"></a>ドライバー バージョンの取得
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  インストールされているのバージョン[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]次の方法で確認できます。  
  
-   呼び出す、 [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)メソッド[getDriverMajorVersion](../../connect/jdbc/reference/getdrivermajorversion-method-sqlserverdatabasemetadata.md)、 [getDriverMinorVersion](../../connect/jdbc/reference/getdriverminorversion-method-sqlserverdatabasemetadata.md)、または[getDriverVersion](../../connect/jdbc/reference/getdriverversion-method-sqlserverdatabasemetadata.md)です。  
  
-   製品配布の readme.txt ファイルにバージョンが表示されます。  
  
 さらに、JDBC ドライバー名を返すことが、 [getDriverName](../../connect/jdbc/reference/getdrivername-method-sqlserverdatabasemetadata.md) SQLServerDatabaseMetaData クラスのメソッドの呼び出しです。 返されます、たとえば、"Microsoft JDBC Driver 6.4 for SQL Server"です。  
  
 SQLServerDatabaseMetaData クラスのメソッドへの呼び出しからには、出力の例を次に示します。  
  
 `getDriverName = Microsoft JDBC Driver 6.4 for SQL Server`  
  
 `getDriverMajorVersion = 6`  
  
 `getDriverMinorVersion = 4`  
  
 `getDriverVersion = 6.4.` *xxx.x*  
  
 「xxx.x」は最終バージョン番号です。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーで発生した問題の診断](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
