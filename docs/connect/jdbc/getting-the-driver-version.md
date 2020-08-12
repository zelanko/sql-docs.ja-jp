---
title: ドライバー バージョンの取得
description: Microsoft JDBC Driver for SQL Server のバージョンを確認する方法と場所について説明します。
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5e241d72-16da-4ada-ac67-e6308394108f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f90f521457f5df17be814a179353d138a3245aea
ms.sourcegitcommit: b2ab989264dd9d23c184f43fff2ec8966793a727
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2020
ms.locfileid: "86381196"
---
# <a name="getting-the-driver-version"></a>ドライバー バージョンの取得
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  インストールされている [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] のバージョンは、次の方法で確認できます。  
  
-   [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) の [getDriverMajorVersion](../../connect/jdbc/reference/getdrivermajorversion-method-sqlserverdatabasemetadata.md) メソッド、[getDriverMinorVersion](../../connect/jdbc/reference/getdriverminorversion-method-sqlserverdatabasemetadata.md) メソッド、または [getDriverVersion](../../connect/jdbc/reference/getdriverversion-method-sqlserverdatabasemetadata.md) メソッドを呼び出します。  
  
-   製品付属の readme.txt ファイルに記載されているバージョンを確認する  
  
 また、SQLServerDatabaseMetaData クラスの [getDriverName](../../connect/jdbc/reference/getdrivername-method-sqlserverdatabasemetadata.md) メソッドを呼び出すと、JDBC ドライバー名が返されます。 たとえば、返されるドライバー名は "Microsoft JDBC Driver 6.4 for SQL Server" です。  
  
 次の例は、SQLServerDatabaseMetaData クラスのメソッドを呼び出して生成される出力の例を示しています。  
  
 `getDriverName = Microsoft JDBC Driver 6.4 for SQL Server`  
  
 `getDriverMajorVersion = 6`  
  
 `getDriverMinorVersion = 4`  
  
 `getDriverVersion = 6.4.` *xxx.x*  
  
 「xxx.x」は最終バージョン番号です。  
  
## <a name="see-also"></a>関連項目  
 [JDBC ドライバーに関する問題の診断](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
