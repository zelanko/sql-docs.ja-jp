---
title: Oracle データベースの SQL Server への移行 (OracleToSQL) |Microsoft Docs
description: SQL Server Migration Assistant (SSMA) を使用して SQL Server または Azure SQL Database に Oracle データベースを移行するには、この推奨プロセスを使用します。
ms.prod: sql
ms.custom: ''
ms.date: 04/22/2018
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 1d196dd6-4322-4c98-bb72-602c57d96134
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 67fb6eeba0a1385d3d764dfa2d8e55f40f34455a
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84294052"
---
# <a name="migrating-oracle-databases-to-sql-server-oracletosql"></a>SQL Server への Oracle のデータの移行 (OracleToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Migration Assistant (SSMA) for Oracle は、Oracle データベースを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、AZURE SQL DB、または Azure SQL Data Warehouse に迅速に移行するのに役立つ包括的な環境です。 SSMA for Oracle を使用すると、データベースオブジェクトとデータの確認、移行のためのデータベースの評価、データベースオブジェクトのへの移行、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] AZURE SQL db、または Azure SQL Data Warehouse、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、AZURE sql db、または Azure SQL Data Warehouse へのデータの移行を行うことができます。 SYS およびシステム Oracle スキーマは移行できないことに注意してください。
  
## <a name="recommended-migration-process"></a>推奨される移行プロセス  
オブジェクトとデータを Oracle データベースから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、AZURE SQL DB、または Azure SQL Data Warehouse に正常に移行するには、次の手順を使用します。
  
1.  [新しい SSMA プロジェクトを作成](working-with-ssma-projects-oracletosql.md)します。  
  
    プロジェクトを作成した後、プロジェクトの変換、移行、および種類のマッピングオプションを設定できます。 プロジェクト設定の詳細については、「[プロジェクトオプションの設定 &#40;OracleToSQL&#41;](../../ssma/oracle/setting-project-options-oracletosql.md)」を参照してください。 データ型マッピングをカスタマイズする方法の詳細については、「 [OracleToSQL&#41;&#40;のデータ型の SQL Server マッピング](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md)」を参照してください。  
  
2.  [Oracle データベースサーバーに接続](connecting-to-oracle-database-oracletosql.md)します。  
  
3.  [SQL Server のインスタンスに接続](connecting-to-sql-server-oracletosql.md)します。  
  
4.  [Oracle データベーススキーマを SQL Server データベーススキーマにマップ](mapping-oracle-schemas-to-sql-server-schemas-oracletosql.md)します。  
  
5.  必要に応じて、[評価レポートを作成](assessing-oracle-schemas-for-conversion-oracletosql.md)して、データベースオブジェクトの変換を評価し、変換時間を見積もることができます。  
  
6.  [Oracle データベーススキーマを SQL Server スキーマに変換](converting-oracle-schemas-oracletosql.md)します。  
  
7.  [変換されたデータベースオブジェクトを SQL Server に読み込み](loading-converted-database-objects-into-sql-server-oracletosql.md)ます。  
  
    これは、次の方法のいずれかで実行できます。  
  
    -   スクリプトを保存し、で実行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。  
  
    -   データベースオブジェクトを同期します。  
  
8.  [SQL Server にデータを移行](migrating-oracle-data-into-sql-server-oracletosql.md)します。  
  
9. 必要に応じて、データベースアプリケーションを更新します。  
  
## <a name="see-also"></a>参照  
[SSMA for Oracle &#40;OracleToSQL のインストール&#41;](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md)  
[SSMA for Oracle &#40;OracleToSQL によるはじめに&#41;](../../ssma/oracle/getting-started-with-ssma-for-oracle-oracletosql.md)  
  
