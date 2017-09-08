---
title: "SQL Server - Azure SQL DB に Sybase ASE データベースの移行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: ed7952d4-8331-44d7-bccf-3440e17238b2
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 63dc9188d93def41a5116386f93bf29e3b744e8e
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="migrating-sybase-ase-databases-to-sql-server---azure-sql-db-sybasetosql"></a>SQL Server - Azure SQL DB (SybaseToSQL) への Sybase ASE データベースの移行
SQL Server Migration Assistant (SSMA) for Sybase は包括的な環境を Sybase Adaptive Server Enterprise (ASE) データベースを簡単に移行するのに役立つ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB します。 SSMA for Sybase を使用することができます、確認するデータベース オブジェクトとデータ、移行対象のデータベースを評価するデータベース オブジェクトを移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB へのデータを移行してから、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB します。  
  
## <a name="recommended-migration-process"></a>移行プロセスを推奨  
ASE データベースからオブジェクトとデータを正常に移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB は、次のプロセスを使用します。  
  
1.  [新しい SSMA プロジェクトを作成](http://msdn.microsoft.com/en-us/11091d95-c488-48c3-891a-743cac94ac93)です。  
  
    プロジェクトを作成した後は、プロジェクトの変換、移行、および種類のマッピング オプションを設定できます。 プロジェクト設定については、次を参照してください。[プロジェクト オプションの設定 & #40 です。SybaseToSQL &#41;](../../ssma/sybase/setting-project-options-sybasetosql.md). データ型マッピングのカスタマイズの概要については、次を参照してください。 [Sybase ASE のマッピングと SQL Server データ型 & #40 です。SybaseToSQL &#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
2.  [Sybase ASE データベース サーバーに接続](http://msdn.microsoft.com/en-us/a45a2330-9175-4c9e-af38-ef920e350614)です。  
  
3.  [SQL Server インスタンスへの接続](http://msdn.microsoft.com/en-us/dd368a1a-45b0-40e9-b4d3-5cdb48c26606)または[Azure SQL DB のインスタンスへの接続](http://msdn.microsoft.com/en-us/9e77e4b0-40c0-455c-8431-ca5d43849aa7)です。  
  
4.  [ASE データベース スキーマを SQL Server にマップします。 Azure SQL DB データベース スキーマ/](http://msdn.microsoft.com/en-us/2c927003-c49d-4fe1-8e3e-5b2899166268)です。  
  
5.  必要に応じて、[評価レポートを作成する](http://msdn.microsoft.com/en-us/eb996b7c-1eef-4f73-b5e6-2fa6faf7336c)変換のためのデータベース オブジェクトを評価し、変換にかかる時間を推定します。  
  
6.  [SQL Server Sybase ASE データベース スキーマに変換/Azure SQL DB スキーマ](http://msdn.microsoft.com/en-us/509cb65d-2f54-427a-83d7-37919cc4e3e3)です。  
  
7.  [変換後のデータベース オブジェクトを読み込む SQL Server と Azure SQL DB](http://msdn.microsoft.com/en-us/4c59256f-99a8-4351-9559-a455813dbd06)です。  
  
    いずれかでスクリプトを保存して実行すること[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]またはデータベース オブジェクトを同期できるの Azure SQL DB、またはします。  
  
8.  [SQL Server にデータを移行または Azure SQL DB](http://msdn.microsoft.com/en-us/54a39f5e-9250-4387-a3ae-eae47c799811)です。  
  
9. 必要に応じて、データベース アプリケーションを更新します。  
  
## <a name="see-also"></a>参照  
[SSMA の Sybase &#40; のインストールSybaseToSQL &#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
[For Sybase &#40; SSMA の概要SybaseToSQL &#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)  
  

