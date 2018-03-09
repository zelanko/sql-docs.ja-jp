---
title: "sys.sysdatabases (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.service: 
ms.component: system-compatibility-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sysdatabases_TSQL
- sys.sysdatabases_TSQL
- sys.sysdatabases
- sysdatabases
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysdatabases compatibility view
- sysdatabases system table
ms.assetid: 60a93880-62f1-4eda-a886-f046706ba90c
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 57ddd4182fcfd3a2d85307df7a898c5d0a66a7e0
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="syssysdatabases-transact-sql"></a>sys.sysdatabases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  インスタンス内の各データベースの 1 つの行を含む[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 ときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が最初にインストールされている**sysdatabases**のエントリが含まれています、**マスター**、**モデル**、 **msdb**、および**tempdb**データベース。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|データベース名|  
|**dbid**|**smallint**|データベース ID|  
|**sid**|**varbinary(85)**|データベース作成者のシステム ID です。|  
|**mode**|**smallint**|データベースの作成中に内部で使用し、データベースをロックします。|  
|**ステータス**|**int**|ステータス ビット、その一部を使用して設定できます[ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md)前述。<br /><br /> 1 = **autoclose** (ALTER DATABASE)<br /><br /> 4 = **select/bulkcopy** (ALTER DATABASE は SET RECOVERY を使用して)<br /><br /> 8 =**間接的に trunc. log** (ALTER DATABASE は SET RECOVERY を使用して)<br /><br /> 16 =**破損ページ検出**(ALTER DATABASE)<br /><br /> 32 = **loading**<br /><br /> 64 =**より前の回復**<br /><br /> 128 = **recovering**<br /><br /> 256 =**は回復されませんでした**<br /><br /> 512 = **offline** (ALTER DATABASE)<br /><br /> 1024 =**読み取り専用**(ALTER DATABASE)<br /><br /> 2048 = **dbo でのみ使用**(ALTER DATABASE は SET RESTRICTED_USER を使用して)<br /><br /> 4096 =**シングル ユーザー** (ALTER DATABASE)<br /><br /> 32768 =**緊急モード**<br /><br /> 65536 = **CHECKSUM** (ALTER DATABASE)<br /><br /> 4194304 = **autoshrink** (ALTER DATABASE)<br /><br /> 1073741824 =**クリーンにシャット ダウン**<br /><br /> 複数のビットが同時にオンであってもかまいません。|  
|**status2**|**int**|16384 = **ANSI null default** (ALTER DATABASE)<br /><br /> 65536 = **concat null yields null** (ALTER DATABASE)<br /><br /> 131, 072 =**再帰トリガー** (ALTER DATABASE)<br /><br /> 1048576 =**ローカル カーソルの既定値は**(ALTER DATABASE)<br /><br /> 8,388, 608 =**識別子を引用符で囲まれた**(ALTER DATABASE)<br /><br /> 33554432 = **cursor close on commit** (ALTER DATABASE)<br /><br /> 67108864 = **ANSI nulls** (ALTER DATABASE)<br /><br /> 268435456 = **ANSI warnings** (ALTER DATABASE)<br /><br /> 536870912 =**完全なテキストが有効な**(を使用して設定**sp_fulltext_database**)|  
|**crdate**|**datetime**|作成日です。|  
|**reserved**|**datetime**|将来の使用のために予約されています。|  
|**category**|**int**|レプリケーションで使用する情報のビットマップです。<br /><br /> 1 = スナップショット レプリケーション用またはトランザクション レプリケーション用にパブリッシュされています。<br /><br /> 2 = スナップショット パブリケーションまたはトランザクション パブリケーションにサブスクライブしています。<br /><br /> 4 = マージ レプリケーション用にパブリッシュされています。<br /><br /> 8 = マージ パブリケーションにサブスクライブしています。<br /><br /> 16 = ディストリビューション データベースです。|  
|**cmptlevel**|**tinyint**|データベースの互換性レベル。 詳細については、「[ALTER DATABASE 互換性レベル &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)」を参照してください。|  
|**filename**|**nvarchar(260)**|データベースのプライマリ ファイルのオペレーティング システム パスと名前です。<br /><br /> **filename**を表示する**dbcreator**、 **sysadmin**、CREATE ANY DATABASE 権限、または、次の権限のいずれかのある権限付与対象ユーザーを持つデータベース所有者: ALTER ANYデータベースの任意のデータベースの作成の定義を表示します。 パスとファイル名を返すクエリ、 [sys.sysfiles](../../relational-databases/system-compatibility-views/sys-sysfiles-transact-sql.md)互換性ビューまたは[sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)ビュー。|  
|**version**|**smallint**|このデータベースが作成された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コードの内部バージョン番号です。 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [システム ビュー &#40; をシステム テーブルのマッピングTRANSACT-SQL と #41 です。](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [互換性ビュー &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
