---
title: Microsoft SQL Server 用 JDBC Driver のダウンロード
description: SQL Server に接続する Java アプリケーションを開発するには、Microsoft SQL Server 用 JDBC Driver をダウンロードします。
ms.date: 09/30/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 451181b8-11e6-4d01-b547-9ac5aada8238
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dc273bccf054408f48e7bb2bd0409a31bb18bd18
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "71682008"
---
# <a name="download-microsoft-jdbc-driver-for-sql-server"></a>Microsoft SQL Server 用 JDBC Driver のダウンロード

この記事では、SQL Server 用 Microsoft JDBC Driver へのダウンロード リンクを提供します。 このドライバーを使用すると、SQL Server に接続する Java アプリケーションを開発できます。  

## <a name="available-downloads-of-jdbc-driver-for-sql-server"></a>JDBC Driver for SQL Server の利用可能なダウンロード

次の表のリンクを使用して、お使いの Java Runtime Environment (JRE) に合った最新の SQL Server 用 Microsoft JDBC Driver をダウンロードしてください。

| Version | リリース日 | Java のバージョン |
|---|---|---|
| [Microsoft JDBC Driver 7.4](https://go.microsoft.com/fwlink/?linkid=2099962) | 8/1/2019 | JRE 8、11、12 |
| [Microsoft JDBC Driver 7.2](https://go.microsoft.com/fwlink/?linkid=2063159) | 4/17/2019 | JRE 8、11 |
| [Microsoft JDBC Driver 7.0](https://go.microsoft.com/fwlink/?linkid=2005972) | 7/31/2018 | JRE 8、10 |
| [Microsoft JDBC Driver 6.4](https://go.microsoft.com/fwlink/?linkid=868290)  | 3/26/2018 | JRE 7、8、9 |
| [Microsoft JDBC Driver 6.2](https://go.microsoft.com/fwlink/?linkid=852460) | 2/12/2018 | JRE 7、8 |
| [Microsoft JDBC Driver 6.0](https://go.microsoft.com/fwlink/?LinkId=245496) | 2/27/2018 | JRE 7、8 |
| [Microsoft JDBC Driver 4.2](https://go.microsoft.com/fwlink/?linkid=841534) | 2/26/2018 | JRE 7、8 |
| [Microsoft JDBC Driver 4.1](https://go.microsoft.com/fwlink/?linkid=841533) | 2/27/2018 | JRE 7 |

ドライバーをダウンロードすると、複数の JAR ファイルがあります。 JAR ファイルの名前は、サポートされている Java のバージョンを示します。 各リリースの詳細については、[リリース ノート](release-notes-for-the-jdbc-driver.md)と[システム要件](system-requirements-for-the-jdbc-driver.md)に関するページを参照してください。

## <a name="using-the-jdbc-driver-with-maven-central"></a>JDBC ドライバーと Maven Central の使用

JDBC ドライバーを Maven プロジェクトに追加するには、次のコードを使って POM.xml ファイルに依存関係としてこれを追加します。

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.4.1.jre11</version>
</dependency>
```  

## <a name="unsupported-drivers"></a>サポートされていないドライバー

サポートされていないバージョンのドライバーは、ここではダウンロードできません。 Microsoft は Java 接続のサポートの向上を継続的に進めています。 そのため、最新バージョンの Microsoft JDBC ドライバーを使用することを強くおすすめします。  
  
## <a name="next-steps"></a>次のステップ

SQL Server 用 Microsoft JDBC Driver の詳細については、「[JDBC ドライバーの概要](overview-of-the-jdbc-driver.md)」と [JDBC ドライバーの GitHub リポジトリ](https://github.com/microsoft/mssql-jdbc/blob/dev/README.md)を参照してください。
