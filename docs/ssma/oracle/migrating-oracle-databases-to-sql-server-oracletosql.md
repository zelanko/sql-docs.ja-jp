---
title: "SQL Server (OracleToSQL) にデータベースを移行する Oracle |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d196dd6-4322-4c98-bb72-602c57d96134
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e4d283fe3329fb7d2a656720e9e6b72583a95f6b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="migrating-oracle-databases-to-sql-server-oracletosql"></a>SQL Server (OracleToSQL) への Oracle データベースの移行
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) for Oracle は Oracle データベースを簡単に移行するのに役立つ包括的な環境[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB します。 SSMA for Oracle を使用することができます、確認するデータベース オブジェクトとデータ、移行対象のデータベースを評価するデータベース オブジェクトを移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB へのデータを移行してから、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB します。 SYS および Oracle のシステム スキーマを移行することはできませんに注意してください。  
  
## <a name="recommended-migration-process"></a>移行プロセスを推奨  
正常に移行するオブジェクトとデータへの Oracle データベースから[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または Azure SQL DB は、次の手順します。  
  
1.  [新しい SSMA プロジェクトを作成](http://msdn.microsoft.com/en-us/ee5d94c0-c7a6-4779-bd32-729bdaf61e1b)です。  
  
    プロジェクトを作成した後は、プロジェクトの変換、移行、および種類のマッピング オプションを設定できます。 プロジェクト設定については、次を参照してください。[プロジェクト オプションの設定 &#40;OracleToSQL"&"#41;](../../ssma/oracle/setting-project-options-oracletosql.md)です。 データ型マッピングをカスタマイズする方法については、次を参照してください。[マッピング Oracle と SQL Server データ型 &#40;OracleToSQL"&"#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md)です。  
  
2.  [Oracle データベース サーバーに接続](http://msdn.microsoft.com/en-us/e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6)です。  
  
3.  [SQL Server のインスタンスに接続](http://msdn.microsoft.com/en-us/1b2a8059-1829-4904-a82f-9c06de1e245f)です。  
  
4.  [SQL Server データベース スキーマに Oracle データベース スキーマをマップ](http://msdn.microsoft.com/en-us/0edeaa08-9c5d-4e3a-bc15-b9a1f0c8a9dc)です。  
  
5.  必要に応じて、[評価レポートを作成する](http://msdn.microsoft.com/en-us/4de9bcf6-1346-4740-87f9-7f24a8226357)変換のためのデータベース オブジェクトを評価し、変換にかかる時間を推定します。  
  
6.  [SQL Server スキーマに Oracle データベース スキーマを変換](http://msdn.microsoft.com/en-us/e021182d-31da-443d-b110-937f5db27272)です。  
  
7.  [SQL Server に変換後のデータベース オブジェクトを読み込む](http://msdn.microsoft.com/en-us/a8ae33b2-1883-4785-922b-ea0e31c0b37a)します。  
  
    これは、次の方法のいずれかで行います。  
  
    -   スクリプトを保存し、実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]です。  
  
    -   データベース オブジェクトを同期します。  
  
8.  [SQL Server にデータを移行](http://msdn.microsoft.com/en-us/e23c5268-41ed-4e55-9fe7-a11376202a13)です。  
  
9. 必要に応じて、データベース アプリケーションを更新します。  
  
## <a name="see-also"></a>参照  
[Oracle &#40;OracleToSQL"&"#41 です。 SSMA をインストールします。](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md)  
[入門 SSMA for Oracle &#40;OracleToSQL"&"#41;](../../ssma/oracle/getting-started-with-ssma-for-oracle-oracletosql.md)  
  

