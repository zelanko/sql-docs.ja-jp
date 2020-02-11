---
title: MySQL データベースを SQL Server に移行する-Azure SQL DB |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8006f9a0-394d-4238-8dc5-44255134628b
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 33dd7faf67e82f1259ac87a0ef8e0eb5fdf2927d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67908796"
---
# <a name="migrating-mysql-databases-to-sql-server---azure-sql-db-mysqltosql"></a>MySQL データベースの SQL Server への移行-Azure SQL DB (MySQLToSql)
SQL Server Migration Assistant (SSMA) for MySQL は、MySQL データベースを SQL Server または SQL Azure にすばやく移行するのに役立つ包括的な環境です。 SSMA for MySQL を使用すると、データベースオブジェクトとデータの確認、データベースオブジェクトの移行の評価、SQL Server または SQL Azure へのデータベースオブジェクトの移行、SQL Server または SQL Azure へのデータの移行を行うことができます。  
  
## <a name="recommended-migration-process"></a>推奨される移行プロセス  
MySQL データベースから SQL Server または SQL Azure にオブジェクトとデータを正常に移行するには、次の手順を使用します。  
  
1.  [SSMA プロジェクトを操作するには &#40;MySQLToSQL&#41;を](../../ssma/mysql/working-with-ssma-projects-mysqltosql.md)使用します。  
  
    プロジェクトを作成した後、プロジェクトの変換、移行、および種類のマッピングオプションを設定できます。 プロジェクト設定の詳細については、「[プロジェクトオプションの設定 &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md)」を参照してください。 データ型マッピングをカスタマイズする方法の詳細については、「 [MySQLToSQL データ型 &#40;&#41;の SQL Server マップ](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)」を参照してください。  
  
2.  [MySQL &#40;MySQLToSQL&#41;に接続しています](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
3.  [SQL Server &#40;MySQLToSQL&#41;に接続しています](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
4.  [MySQL データベースを SQL Server スキーマ &#40;MySQLToSQL&#41;にマッピングする](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
5.  [Azure SQL DB &#40;MySQLToSQL&#41;に接続しています](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
  
6.  必要に応じて、 [MySQLToSQL&#41;への変換のために MySQL データベースを評価](../../ssma/mysql/assessing-mysql-databases-for-conversion-mysqltosql.md)して、変換対象のデータベースオブジェクトを評価し、変換時間を見積もる &#40;ます。  
  
7.  [MySQL データベース &#40;MySQLToSQL&#41;に変換しています](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
8.  [Synchronization](loading-converted-database-objects-into-sql-server-mysqltosql.md)  
  
9. これは、次の方法のいずれかで実行できます。  
  
    -   スクリプトを保存し、SQL Server または SQL Azure で実行します。  
  
    -   データベースオブジェクトを同期します。  
  
10. [MySQL データの SQL Server への移行-Azure SQL DB &#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
11. 必要に応じて、データベースアプリケーションを更新します。  
  
> [!NOTE]  
> Information_schema および MySQL スキーマを移行することはできません。  
  
## <a name="see-also"></a>参照  
[SSMA for MySQL のインストール &#40;MySqlToSql&#41;](../../ssma/mysql/installing-ssma-for-mysql-mysqltosql.md)  
[SSMA for MySQL のはじめに &#40;MySQLToSQL&#41;](../../ssma/mysql/getting-started-with-ssma-for-mysql-mysqltosql.md)  
  
