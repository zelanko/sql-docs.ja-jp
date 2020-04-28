---
title: Sybase ASE データベースを SQL Server に移行する-Azure SQL DB |Microsoft Docs
ms.custom: ''
ms.date: 11/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: ed7952d4-8331-44d7-bccf-3440e17238b2
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: c3735e03e3196f899ab33ca152364244e3331ac5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68028852"
---
# <a name="migrating-sap-ase-databases-to-sql-server---azure-sql-database-sybasetosql"></a>SQL Server Azure SQL Database への SAP ASE データベースの移行 (SybaseToSQL)
SAP Adaptive Server Enterprise (ASE) の SQL Server Migration Assistant (SSMA) は、SAP ASE データベースをまたは Azure SQL Database に迅速に移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]するのに役立つ包括的な環境です。 SSMA for SAP ASE を使用することにより、データベースオブジェクトとデータを確認し、データベースの移行を評価[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]し、データベースオブジェクトをまたは Azure SQL Database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に移行した後、データをまたは Azure SQL Database に移行できます。  
  
## <a name="recommended-migration-process"></a>推奨される移行プロセス  
オブジェクトとデータを SAP ASE データベースからまたは Azure SQL Database [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に正常に移行するには、次の手順を使用します。  
  
1.  [新しい SSMA プロジェクトを作成](working-with-ssma-projects-sybasetosql.md)します。  
  
    プロジェクトを作成した後、プロジェクトの変換、移行、および種類のマッピングオプションを設定できます。 プロジェクト設定の詳細については、「 [SybaseToSQL&#41;&#40;プロジェクトオプションの設定](../../ssma/sybase/setting-project-options-sybasetosql.md)」を参照してください。 データ型マッピングのカスタマイズの詳細については、「 [SQL&#41;の SYBASE ASE と SQL Server のデータ &#40;型のマッピング](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md)」を参照してください。  
  
2.  [SAP ASE データベースサーバーに接続](connecting-to-sybase-ase-sybasetosql.md)します。  
  
3.  [インスタンス SQL Server に接続する](connecting-to-sql-server-sybasetosql.md)か[、Azure SQL Database のインスタンスに接続](connecting-to-azure-sql-db-sybasetosql.md)します。  
  
4.  [SAP ASE データベーススキーマを SQL Server/Azure SQL Database データベーススキーマにマップ](https://msdn.microsoft.com/2c927003-c49d-4fe1-8e3e-5b2899166268)します。  
  
5.  必要に応じて、[評価レポートを作成](assessing-sybase-ase-database-objects-for-conversion-sybasetosql.md)して、データベースオブジェクトの変換を評価し、変換時間を見積もることができます。  
  
6.  [SAP ASE データベーススキーマを SQL Server/Azure SQL Database スキーマに変換](https://msdn.microsoft.com/509cb65d-2f54-427a-83d7-37919cc4e3e3)します。  
  
7.  [変換されたデータベースオブジェクトを SQL Server/Azure SQL Database に読み込み](https://msdn.microsoft.com/4c59256f-99a8-4351-9559-a455813dbd06)ます。  
  
    スクリプトを保存して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または Azure SQL Database に実行するか、データベースオブジェクトを同期します。  
  
8.  [SQL Server/Azure SQL Database にデータを移行](https://msdn.microsoft.com/54a39f5e-9250-4387-a3ae-eae47c799811)します。  
  
9. 必要に応じて、データベースアプリケーションを更新します。  
  
## <a name="see-also"></a>関連項目  
[SSMA for SAP ASE のインストール &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
[SSMA for SAP ASE のはじめに &#40;SybaseToSQL&#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)  
  
