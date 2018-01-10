---
title: "SQL Server 2016 におけるデータベース エンジン機能の重大な変更 | Microsoft Docs"
ms.custom: 
ms.date: 11/15/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: database-engine
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Database Engine [SQL Server], what's new
- breaking changes [SQL Server]
ms.assetid: 47edefbd-a09b-4087-937a-453cd5c6e061
caps.latest.revision: "144"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 2c406943e49924d383807cf0848d71d51fe47080
ms.sourcegitcommit: 719bcc010dd1ca6f2acfcdf6f9bd9f73451ca8ca
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="breaking-changes-to-database-engine-features-in-sql-server-2016"></a>SQL Server 2016 におけるデータベース エンジン機能の重大な変更
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  このトピックでは、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)][!INCLUDE[ssDE](../includes/ssde-md.md)] 以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]における重大な変更について説明します。 これらの変更によって、以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に基づくアプリケーション、スクリプト、または機能が使用できなくなる場合があります。 この問題は、アップグレードするときに発生することがあります。  
  
##  <a name="SQL15"></a> [!INCLUDE[ssSQL15](../includes/sssql15-md.md)] における重大な変更  
  
-   sys.dm_io_virtual_file_stats の sample_ms 列が **int** データ型から **bigint** データ型に拡張されました。  
  
-   sys.fn_virtualfilestats の TimeStamp 列が **int** データ型から **bigint** データ型に拡張されました。  

-   MD2、MD4、MD5、SHA、または SHA1 ハッシュ アルゴリズム (非推奨) を使用するには、データベース互換性レベルを 130 より前に設定する必要があります。  

-   データベース互換性レベル 130 の下で、 **datetime** から **datetime2** にデータ型を暗黙的に変換するとき、精度が上がります。小数ミリ秒が計算に入り、結果的にさまざまな変換値が生成されます。 datetime データ型と datetime2 データ型の間で混合比較シナリオが存在する場合、datetime2 データ型への明示的型変換を使用します。 詳細については、この [Microsoft サポート技術情報](http://support.microsoft.com/help/4010261)を参照してください。
  
## <a name="previous-versions"></a>以前のバージョン  
  
-   [SQL Server 2014 におけるデータベース エンジン機能の重大な変更](https://msdn.microsoft.com/library/ms143179\(v=sql.120\))  
  
-   [SQL Server 2012 におけるデータベース エンジン機能の重大な変更](https://msdn.microsoft.com/library/ms143179\(v=sql.110\))  
  
-   [SQL Server 2008 におけるデータベース エンジン機能の重大な変更](https://msdn.microsoft.com/library/ms143179\(v=sql.100\))  
  
## <a name="see-also"></a>参照  
 [SQL Server 2016 データベース エンジンの非推奨機能](../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)   
 [SQL Server 2016 で廃止されたデータベース エンジンの機能](../database-engine/discontinued-database-engine-functionality-in-sql-server-2016.md)   
 [SQL Server データベース エンジンの旧バージョンとの互換性](../database-engine/sql-server-database-engine-backward-compatibility.md)   
 [ALTER DATABASE 互換性レベル &#40;Transact-SQL&#41;](../t-sql/statements/alter-database-transact-sql-compatibility-level.md)   
 [いくつかのデータ型と一般的でない操作を処理するときの SQL Server と Azure の SQL データベースの機能強化](http://support.microsoft.com/help/4010261)
  
  
