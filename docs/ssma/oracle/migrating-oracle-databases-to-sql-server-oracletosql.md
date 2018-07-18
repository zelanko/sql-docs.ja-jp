---
title: SQL Server (OracleToSQL) にデータベースの移行の Oracle |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 04/22/2018
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1d196dd6-4322-4c98-bb72-602c57d96134
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: f20b7271932cbbcc0538fc9923e45b2fc029f646
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38983204"
---
# <a name="migrating-oracle-databases-to-sql-server-oracletosql"></a>SQL Server (OracleToSQL) に Oracle データベースを移行します。
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Migration Assistant (SSMA) for Oracle は Oracle データベースを迅速に移行するのに役立つ包括的な環境[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、Azure SQL DB、または Azure SQL Data Warehouse。 SSMA for Oracle を使用してデータベース オブジェクトとデータを確認して、移行対象のデータベースを評価をするデータベース オブジェクトを移行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、Azure SQL DB、または Azure SQL Data Warehouse へのデータを移行し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、Azure SQL DB、または Azure SQL データウェアハウス。 SYS および Oracle のシステム スキーマを移行することはできませんに注意してください。
  
## <a name="recommended-migration-process"></a>移行プロセスをお勧めします。  
Oracle データベースからオブジェクトとデータを正常に移行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、Azure SQL DB、または Azure SQL Data Warehouse では、次のプロセスを使用します。
  
1.  [新しい SSMA プロジェクト作成](http://msdn.microsoft.com/ee5d94c0-c7a6-4779-bd32-729bdaf61e1b)です。  
  
    プロジェクトを作成した後は、プロジェクトの変換、移行、およびオプションのマッピングの種類を設定できます。 プロジェクトの設定については、次を参照してください。[プロジェクト オプションの設定&#40;OracleToSQL&#41;](../../ssma/oracle/setting-project-options-oracletosql.md)します。 データ型のマッピングをカスタマイズする方法については、次を参照してください。[マッピング Oracle および SQL Server データ型&#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md)します。  
  
2.  [Oracle データベース サーバーに接続する](http://msdn.microsoft.com/e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6)します。  
  
3.  [SQL Server のインスタンスに接続する](http://msdn.microsoft.com/1b2a8059-1829-4904-a82f-9c06de1e245f)します。  
  
4.  [SQL Server データベースのスキーマに Oracle データベース スキーマを割り当てる](http://msdn.microsoft.com/0edeaa08-9c5d-4e3a-bc15-b9a1f0c8a9dc)します。  
  
5.  必要に応じて、[評価レポートを作成する](http://msdn.microsoft.com/4de9bcf6-1346-4740-87f9-7f24a8226357)変換のためのデータベース オブジェクトを評価し、変換にかかる時間を推定します。  
  
6.  [SQL Server スキーマに Oracle データベース スキーマを変換](http://msdn.microsoft.com/e021182d-31da-443d-b110-937f5db27272)します。  
  
7.  [SQL Server に変換されたデータベース オブジェクトを読み込む](http://msdn.microsoft.com/a8ae33b2-1883-4785-922b-ea0e31c0b37a)します。  
  
    これは、次の方法のいずれかで行います。  
  
    -   スクリプトを保存しで実行[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]します。  
  
    -   データベース オブジェクトを同期します。  
  
8.  [SQL Server にデータを移行](http://msdn.microsoft.com/e23c5268-41ed-4e55-9fe7-a11376202a13)します。  
  
9. 必要に応じて、データベース アプリケーションを更新します。  
  
## <a name="see-also"></a>参照  
[SSMA for Oracle のインストール&#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md)  
[Ssma for Oracle 作業の開始&#40;OracleToSQL&#41;](../../ssma/oracle/getting-started-with-ssma-for-oracle-oracletosql.md)  
  
