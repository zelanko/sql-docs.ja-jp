---
title: SQL Server - Azure SQL DB に MySQL データベースの移行 |Microsoft ドキュメント
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 8006f9a0-394d-4238-8dc5-44255134628b
caps.latest.revision: 12
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 1914549671a4a9ccd78ce859f59f55e5a9f9a3e4
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34776738"
---
# <a name="migrating-mysql-databases-to-sql-server---azure-sql-db-mysqltosql"></a>SQL Server - Azure SQL DB (MySQLToSql) への MySQL データベースの移行
SQL Server Migration Assistant (SSMA) for MySQL は、SQL Server または SQL Azure に迅速に MySQL データベースを移行するのに役立つ包括的な環境です。 SSMA for MySQL を使用してデータベース オブジェクトとデータを確認、移行対象のデータベースの評価、SQL Server または SQL Azure にデータベース オブジェクトを移行でき、SQL Server または SQL Azure にデータを移行できます。  
  
## <a name="recommended-migration-process"></a>移行プロセスを推奨  
正常に移行するオブジェクトとデータの MySQL データベースから SQL Server または SQL Azure に、次の手順に従います。  
  
1.  [SSMA プロジェクトでの作業&#40;MySQLToSQL&#41;](../../ssma/mysql/working-with-ssma-projects-mysqltosql.md)です。  
  
    プロジェクトを作成した後は、プロジェクトの変換、移行、および種類のマッピング オプションを設定できます。 プロジェクト設定の詳細については、次を参照してください。[プロジェクト オプションの設定&#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md)です。 データ型マッピングをカスタマイズする方法については、次を参照してください[マッピング MySQL および SQL Server データ型&#40;MySQLToSQL。&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
2.  [MySQL への接続&#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
3.  [SQL Server に接続する&#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
4.  [MySQL データベースを SQL Server スキーマにマッピング&#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
5.  [Azure SQL DB に接続する&#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
  
6.  必要に応じて、[変換用の MySQL データベースの評価&#40;MySQLToSQL&#41; ](../../ssma/mysql/assessing-mysql-databases-for-conversion-mysqltosql.md)変換のためのデータベース オブジェクトを評価し、変換にかかる時間を推定します。  
  
7.  [MySQL データベースを変換する&#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
8.  [同期](http://msdn.microsoft.com/en-us/ac993a6d-0283-4823-8793-6b217677dfa3)  
  
9. これは、次の方法のいずれかで行います。  
  
    -   スクリプトを保存し、SQL Server または SQL Azure で実行します。  
  
    -   データベース オブジェクトを同期します。  
  
10. [SQL Server - Azure SQL DB に MySQL データの移行&#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
11. 必要に応じて、データベース アプリケーションを更新します。  
  
> [!NOTE]  
> Information_schema と MySQL のスキーマを移行することはできません。  
  
## <a name="see-also"></a>参照  
[SSMA の mysql インストール&#40;MySqlToSql&#41;](../../ssma/mysql/installing-ssma-for-mysql-mysqltosql.md)  
[入門 SSMA for MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/getting-started-with-ssma-for-mysql-mysqltosql.md)  
  
