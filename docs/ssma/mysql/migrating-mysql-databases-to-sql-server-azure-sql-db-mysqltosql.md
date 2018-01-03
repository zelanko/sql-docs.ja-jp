---
title: "SQL Server - Azure SQL DB に MySQL データベースの移行 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-mysql
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 8006f9a0-394d-4238-8dc5-44255134628b
caps.latest.revision: "12"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 3e2f0f13d57b242e9f17b7241a1311df17b39612
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="migrating-mysql-databases-to-sql-server---azure-sql-db-mysqltosql"></a>SQL Server - Azure SQL DB (MySQLToSql) への MySQL データベースの移行
SQL Server Migration Assistant (SSMA) for MySQL は、SQL Server または SQL Azure に迅速に MySQL データベースを移行するのに役立つ包括的な環境です。 SSMA for MySQL を使用してデータベース オブジェクトとデータを確認、移行対象のデータベースの評価、SQL Server または SQL Azure にデータベース オブジェクトを移行でき、SQL Server または SQL Azure にデータを移行できます。  
  
## <a name="recommended-migration-process"></a>移行プロセスを推奨  
正常に移行するオブジェクトとデータの MySQL データベースから SQL Server または SQL Azure に、次の手順に従います。  
  
1.  [SSMA プロジェクト &#40; の操作MySQLToSQL &#41;](../../ssma/mysql/working-with-ssma-projects-mysqltosql.md).  
  
    プロジェクトを作成した後は、プロジェクトの変換、移行、および種類のマッピング オプションを設定できます。 プロジェクト設定の詳細については、次を参照してください。[プロジェクト オプションの設定 &#40;です。MySQLToSQL &#41;](../../ssma/mysql/setting-project-options-mysqltosql.md). データ型マッピングをカスタマイズする方法については、次を参照してください。[マッピング MySQL および SQL Server データ型 &#40;です。MySQLToSQL &#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
2.  [MySQL &#40; に接続します。MySQLToSQL &#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
3.  [SQL Server &#40; に接続します。MySQLToSQL &#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
4.  [MySQL データベースを SQL Server スキーマ &#40; にマッピングMySQLToSQL &#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
5.  [Azure SQL DB &#40; に接続します。MySQLToSQL &#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
  
6.  必要に応じて、[変換 &#40; の MySQL データベースを評価します。MySQLToSQL &#41;](../../ssma/mysql/assessing-mysql-databases-for-conversion-mysqltosql.md)変換のためのデータベース オブジェクトを評価し、変換にかかる時間を推定します。  
  
7.  [MySQL データベース &#40; を変換します。MySQLToSQL &#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
8.  [同期](http://msdn.microsoft.com/en-us/ac993a6d-0283-4823-8793-6b217677dfa3)  
  
9. これは、次の方法のいずれかで行います。  
  
    -   スクリプトを保存し、SQL Server または SQL Azure で実行します。  
  
    -   データベース オブジェクトを同期します。  
  
10. [SQL Server - Azure SQL DB &#40; に MySQL データの移行MySQLToSQL &#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
11. 必要に応じて、データベース アプリケーションを更新します。  
  
> [!NOTE]  
> Information_schema と MySQL のスキーマを移行することはできません。  
  
## <a name="see-also"></a>参照  
[SSMA の MySQL &#40; のインストールMySqlToSql &#41;](../../ssma/mysql/installing-ssma-for-mysql-mysqltosql.md)  
[MySQL &#40; for SSMA の概要MySQLToSQL &#41;](../../ssma/mysql/getting-started-with-ssma-for-mysql-mysqltosql.md)  
  
