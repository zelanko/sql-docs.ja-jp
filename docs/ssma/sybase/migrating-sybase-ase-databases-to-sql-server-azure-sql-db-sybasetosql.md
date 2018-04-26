---
title: SQL Server - Azure SQL DB に Sybase ASE データベースの移行 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/30/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-sybase
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: ed7952d4-8331-44d7-bccf-3440e17238b2
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 72e976ecba4c6b8e91a34a141047e36b2a708db4
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="migrating-sap-ase-databases-to-sql-server---azure-sql-database-sybasetosql"></a>SQL Server - Azure SQL データベース (SybaseToSQL) に SAP ASE データベースを移行します。
SQL Server Migration Assistant (SSMA) の SAP Adaptive Server Enterprise (ASE) は、包括的な環境に SAP ASE データベースを簡単に移行するのに役立つ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースです。 SSMA の SAP ASE を使用することができます、確認するデータベース オブジェクトとデータ、移行対象のデータベースを評価するデータベース オブジェクトを移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースへのデータを移行してから、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースです。  
  
## <a name="recommended-migration-process"></a>推奨される移行プロセス  
正常に移行するオブジェクトとデータへの SAP ASE データベースから[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベースは、次の手順します。  
  
1.  [新しい SSMA プロジェクトを作成](http://msdn.microsoft.com/en-us/11091d95-c488-48c3-891a-743cac94ac93)です。  
  
    プロジェクトを作成した後は、プロジェクトの変換、移行、および種類のマッピング オプションを設定できます。 プロジェクト設定については、次を参照してください。[プロジェクト オプションの設定&#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md)です。 データ型マッピングのカスタマイズの概要については、次を参照してください。 [Sybase ASE のマッピング、および SQL Server データ型&#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md)です。  
  
2.  [SAP ASE データベース サーバーに接続](http://msdn.microsoft.com/en-us/a45a2330-9175-4c9e-af38-ef920e350614)です。  
  
3.  [SQL Server インスタンスへの接続](http://msdn.microsoft.com/en-us/dd368a1a-45b0-40e9-b4d3-5cdb48c26606)または[Azure SQL データベースのインスタンスへの接続](http://msdn.microsoft.com/en-us/9e77e4b0-40c0-455c-8431-ca5d43849aa7)です。  
  
4.  [SAP ASE データベース スキーマを SQL Server にマップします。 Azure SQL Database のデータベース スキーマ/](http://msdn.microsoft.com/en-us/2c927003-c49d-4fe1-8e3e-5b2899166268)です。  
  
5.  必要に応じて、[評価レポートを作成する](http://msdn.microsoft.com/en-us/eb996b7c-1eef-4f73-b5e6-2fa6faf7336c)変換のためのデータベース オブジェクトを評価し、変換にかかる時間を推定します。  
  
6.  [SQL Server に SAP ASE データベース スキーマに変換/Azure SQL データベースのスキーマ](http://msdn.microsoft.com/en-us/509cb65d-2f54-427a-83d7-37919cc4e3e3)です。  
  
7.  [変換後のデータベース オブジェクトを読み込む SQL Server と Azure SQL Database](http://msdn.microsoft.com/en-us/4c59256f-99a8-4351-9559-a455813dbd06)です。  
  
    スクリプトを保存するかで実行して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL データベース、またはデータベース オブジェクトを同期します。  
  
8.  [SQL Server にデータを移行または Azure SQL Database](http://msdn.microsoft.com/en-us/54a39f5e-9250-4387-a3ae-eae47c799811)です。  
  
9. 必要に応じて、データベース アプリケーションを更新します。  
  
## <a name="see-also"></a>参照  
[SAP ASE 用 SSMA をインストールする&#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
[SAP ASE for SSMA の概要&#40;SybaseToSQL&#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)  
  
