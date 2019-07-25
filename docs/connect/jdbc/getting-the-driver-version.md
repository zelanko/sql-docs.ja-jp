---
title: ドライバーのバージョンを取得する |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5e241d72-16da-4ada-ac67-e6308394108f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c75f14ca3f24a97240d7430210ab79c70e0bac85
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67956550"
---
# <a name="getting-the-driver-version"></a>ドライバー バージョンの取得
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  インストールされている [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] のバージョンは、次の方法で確認できます。  
  
-   [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) の [getDriverMajorVersion](../../connect/jdbc/reference/getdrivermajorversion-method-sqlserverdatabasemetadata.md) メソッド、[getDriverMinorVersion](../../connect/jdbc/reference/getdriverminorversion-method-sqlserverdatabasemetadata.md) メソッド、または [getDriverVersion](../../connect/jdbc/reference/getdriverversion-method-sqlserverdatabasemetadata.md) メソッドを呼び出します。  
  
-   製品付属の readme.txt ファイルに記載されているバージョンを確認する  
  
 また、SQLServerDatabaseMetaData クラスの [getDriverName](../../connect/jdbc/reference/getdrivername-method-sqlserverdatabasemetadata.md) メソッドを呼び出すと、JDBC ドライバー名が返されます。 たとえば、返されるドライバー名は "Microsoft JDBC Driver 6.4 for SQL Server" です。  
  
 SQLServerDatabaseMetaData クラスのメソッドの呼び出しからの出力の例を次に示します。  
  
 `getDriverName = Microsoft JDBC Driver 6.4 for SQL Server`  
  
 `getDriverMajorVersion = 6`  
  
 `getDriverMinorVersion = 4`  
  
 `getDriverVersion = 6.4.` *xxx.x*  
  
 「xxx.x」は最終バージョン番号です。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーで発生した問題の診断](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
