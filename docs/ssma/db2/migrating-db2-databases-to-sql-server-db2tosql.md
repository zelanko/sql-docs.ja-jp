---
title: SQL Server (DB2ToSQL) にデータベースを移行する DB2 |Microsoft ドキュメント
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-db2
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 14d2e655-af7e-4aa5-ba28-0e3d0d025518
caps.latest.revision: 4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: c908cafeb92acc982bb74d96c4cc6fc2f40bf9a6
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/06/2018
---
# <a name="migrating-db2-databases-to-sql-server-db2tosql"></a>SQL Server (DB2ToSQL) への DB2 データベースの移行
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) for DB2 は、包括的な環境への DB2 データベースを簡単に移行するのに役立つ[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB します。 SSMA for DB2 を使用することができます、確認するデータベース オブジェクトとデータ、移行対象のデータベースを評価するデータベース オブジェクトを移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB へのデータを移行してから、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB します。 SYS およびシステムの DB2 スキーマを移行することはできませんに注意してください。  
  
## <a name="recommended-migration-process"></a>移行プロセスを推奨  
正常に移行するオブジェクトとデータを DB2 データベースから[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB は、次のプロセスを使用します。  
  
1.  [新しい SSMA プロジェクト](http://msdn.microsoft.com/en-us/66437b45-4686-4fc7-a91b-ebde45e0f1b0)です。  
  
    プロジェクトを作成した後は、プロジェクトの変換、移行、および種類のマッピング オプションを設定できます。 プロジェクト設定については、次を参照してください。[プロジェクト設定&#40;変換&#41; &#40;DB2ToSQL&#41; ](../../ssma/db2/project-settings-conversion-db2tosql.md)セクションを関連するとします。 データ型マッピングをカスタマイズする方法については、次を参照してください。[マッピング DB2 および SQL Server データ型&#40;DB2ToSQL&#41;](../../ssma/db2/mapping-db2-and-sql-server-data-types-db2tosql.md)です。  
  
2.  [DB2 データベースに接続](http://msdn.microsoft.com/en-us/5eb5801d-f0c3-4127-97c0-0b1ef49f4844)です。  
  
3.  [SQL Server に接続する](http://msdn.microsoft.com/en-us/b59803cb-3cc6-41cc-8553-faf90851410e)です。  
  
4.  [SQL Server スキーマに DB2 スキーマをマップ](http://msdn.microsoft.com/en-us/05ff7bd4-e60b-4f48-a893-bc2346aa9a8a)です。  
  
5.  必要に応じて、[評価レポート](http://msdn.microsoft.com/en-us/9e13eba0-e3cf-4205-974f-c00f982061de)変換のためのデータベース オブジェクトを評価し、変換にかかる時間を推定します。  
  
6.  [DB2 スキーマを変換](http://msdn.microsoft.com/en-us/7947efc3-ca86-4ec5-87ce-7603059c75a0)です。  
  
7.  [SQL Server に変換後のデータベース オブジェクトを読み込む](http://msdn.microsoft.com/en-us/f4ea1ced-9f9f-4a9d-88ab-81dbab64adc3)します。  
  
    これは、次の方法のいずれかで行います。  
  
    -   スクリプトを保存し、実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
    -   データベース オブジェクトを同期します。  
  
8.  [SQL Server に DB2 データを移行する](http://msdn.microsoft.com/en-us/86cbd39f-6dac-409a-9ce1-7dd54403f84b)です。  
  
9. 必要に応じて、データベース アプリケーションを更新します。  
  
## <a name="see-also"></a>参照  
[SSMA の DB2 のインストール&#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-db2tosql.md)  
[DB2 for SSMA の概要&#40;DB2ToSQL&#41;](../../ssma/db2/getting-started-with-ssma-for-db2-db2tosql.md)  
  
