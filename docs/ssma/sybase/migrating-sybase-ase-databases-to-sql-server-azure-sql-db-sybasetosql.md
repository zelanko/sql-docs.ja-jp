---
title: SQL Server - Azure SQL DB への Sybase ASE データベースの移行 |Microsoft Docs
ms.custom: ''
ms.date: 11/30/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: ed7952d4-8331-44d7-bccf-3440e17238b2
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: a021ac1cfc442943b15ade737c54d0b9e227ef03
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982214"
---
# <a name="migrating-sap-ase-databases-to-sql-server---azure-sql-database-sybasetosql"></a>SQL Server - Azure SQL Database (SybaseToSQL) に SAP ASE データベースを移行します。
SQL Server Migration Assistant (SSMA) for SAP Adaptive Server Enterprise (ASE) は、すぐに SAP ASE データベースを移行するのに役立つ包括的な環境[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL Database。 SAP ASE の SSMA を使用してデータベース オブジェクトとデータを確認して、移行対象のデータベースを評価をするデータベース オブジェクトを移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]や Azure SQL Database へのデータを移行および[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL Database。  
  
## <a name="recommended-migration-process"></a>推奨される移行プロセス  
SAP ASE データベースからオブジェクトとデータを正常に移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL Database に、次のプロセスを使用します。  
  
1.  [新しい SSMA プロジェクト作成](http://msdn.microsoft.com/11091d95-c488-48c3-891a-743cac94ac93)です。  
  
    プロジェクトを作成した後は、プロジェクトの変換、移行、およびオプションのマッピングの種類を設定できます。 プロジェクトの設定については、次を参照してください。[プロジェクト オプションの設定&#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md)します。 データ型のマッピングをカスタマイズする方法については、次を参照してください。[マッピングの Sybase ASE と SQL Server データ型&#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md)します。  
  
2.  [SAP ASE データベース サーバーに接続する](http://msdn.microsoft.com/a45a2330-9175-4c9e-af38-ef920e350614)します。  
  
3.  [SQL Server インスタンスへの接続](http://msdn.microsoft.com/dd368a1a-45b0-40e9-b4d3-5cdb48c26606)または[Azure SQL Database のインスタンスへの接続](http://msdn.microsoft.com/9e77e4b0-40c0-455c-8431-ca5d43849aa7)します。  
  
4.  [SQL Server に SAP ASE データベース スキーマを割り当てる Azure SQL Database のデータベース スキーマ/](http://msdn.microsoft.com/2c927003-c49d-4fe1-8e3e-5b2899166268)します。  
  
5.  必要に応じて、[評価レポートを作成する](http://msdn.microsoft.com/eb996b7c-1eef-4f73-b5e6-2fa6faf7336c)変換のためのデータベース オブジェクトを評価し、変換にかかる時間を推定します。  
  
6.  [SQL Server に SAP ASE データベース スキーマを変換/Azure SQL Database スキーマ](http://msdn.microsoft.com/509cb65d-2f54-427a-83d7-37919cc4e3e3)します。  
  
7.  [SQL Server に変換されたデータベース オブジェクトを読み込むと Azure SQL Database](http://msdn.microsoft.com/4c59256f-99a8-4351-9559-a455813dbd06)します。  
  
    スクリプトを保存するかで実行して[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL Database、またはデータベース オブジェクトを同期します。  
  
8.  [SQL Server にデータを移行または Azure SQL Database](http://msdn.microsoft.com/54a39f5e-9250-4387-a3ae-eae47c799811)します。  
  
9. 必要に応じて、データベース アプリケーションを更新します。  
  
## <a name="see-also"></a>参照  
[SSMA for SAP ASE のインストール&#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
[SSMA で SAP ASE の概要&#40;SybaseToSQL&#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)  
  
