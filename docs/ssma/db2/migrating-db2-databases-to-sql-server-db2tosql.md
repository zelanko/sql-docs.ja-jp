---
title: DB2 データベースの SQL Server への移行 (DB2ToSQL) |Microsoft Docs
description: SQL Server Migration Assistant (SSMA) を使用して SQL Server または Azure SQL Database に DB2 データベースを移行するには、この推奨プロセスを使用します。
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 14d2e655-af7e-4aa5-ba28-0e3d0d025518
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: a351723f12261e07c4cdbd1d707224278067522e
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84293679"
---
# <a name="migrating-db2-databases-to-sql-server-db2tosql"></a>DB2 データベースの SQL Server への移行 (DB2ToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Migration Assistant (SSMA) for DB2 は、DB2 データベースを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE SQL DB にすばやく移行するのに役立つ包括的な環境です。 SSMA for DB2 を使用することにより、データベースオブジェクトとデータの確認、移行のためのデータベースの評価、データベースオブジェクトの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE SQL db への移行、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] または AZURE sql db へのデータの移行を行うことができます。 SYS スキーマとシステム DB2 スキーマは移行できないことに注意してください。  
  
## <a name="recommended-migration-process"></a>推奨される移行プロセス  
オブジェクトとデータを DB2 データベースからまたは Azure SQL DB に正常に移行するに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、次の手順を使用します。  
  
1.  [新しい SSMA プロジェクト](https://msdn.microsoft.com/66437b45-4686-4fc7-a91b-ebde45e0f1b0)。  
  
    プロジェクトを作成した後、プロジェクトの変換、移行、および種類のマッピングオプションを設定できます。 プロジェクト設定の詳細については、「[プロジェクトの設定 &#40;変換&#41; &#40;DB2ToSQL&#41;](../../ssma/db2/project-settings-conversion-db2tosql.md) 」および関連するセクションを参照してください。 データ型マッピングをカスタマイズする方法の詳細については、「 [MAPPING DB2 and SQL Server Data Types &#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md)」を参照してください。  
  
2.  [DB2 データベースに接続](https://msdn.microsoft.com/5eb5801d-f0c3-4127-97c0-0b1ef49f4844)します。  
  
3.  [SQL Server に接続](https://msdn.microsoft.com/b59803cb-3cc6-41cc-8553-faf90851410e)しています。  
  
4.  [DB2 スキーマを SQL Server スキーマにマップ](https://msdn.microsoft.com/05ff7bd4-e60b-4f48-a893-bc2346aa9a8a)します。  
  
5.  必要に応じて、[評価レポート](https://msdn.microsoft.com/9e13eba0-e3cf-4205-974f-c00f982061de)を使用してデータベースオブジェクトの変換を評価し、変換時間を推定します。  
  
6.  [DB2 スキーマを変換](https://msdn.microsoft.com/7947efc3-ca86-4ec5-87ce-7603059c75a0)します。  
  
7.  [変換されたデータベースオブジェクトを SQL Server に読み込み](https://msdn.microsoft.com/f4ea1ced-9f9f-4a9d-88ab-81dbab64adc3)ます。  
  
    これは、次の方法のいずれかで実行できます。  
  
    -   スクリプトを保存し、で実行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] します。  
  
    -   データベースオブジェクトを同期します。  
  
8.  [DB2 データを SQL Server に移行](https://msdn.microsoft.com/86cbd39f-6dac-409a-9ce1-7dd54403f84b)する。  
  
9. 必要に応じて、データベースアプリケーションを更新します。  
  
## <a name="see-also"></a>参照  
[SSMA for DB2 &#40;DB2ToSQL&#41;のインストール](../../ssma/db2/installing-ssma-for-db2-db2tosql.md)  
[SSMA for DB2 &#40;DB2ToSQL のはじめに&#41;](../../ssma/db2/getting-started-with-ssma-for-db2-db2tosql.md)  
  
