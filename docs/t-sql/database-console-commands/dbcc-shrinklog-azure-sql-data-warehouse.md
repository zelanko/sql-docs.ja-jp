---
title: DBCC SHRINKLOG (Parallel Data Warehouse) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2018
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|database-console-commands
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
caps.latest.revision: 11
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ed5957f1ce77f14cf3231702c1b268c75dc5841d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="dbcc-shrinklog-parallel-data-warehouse"></a>DBCC SHRINKLOG (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

現在の [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] データベースの "*アプライアンス全体*" でトランザクション ログのサイズを減らします。 トランザクション ログの圧縮するのには、データを最適化します。 時間の経過と共には、データベースのトランザクション ログが断片化されていない、非効率なになります。 断片化を軽減し、ログのサイズを小さくには、DBCC SHRINKLOG を使用します。
  
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```sql
DBCC SHRINKLOG   
    [ ( SIZE = { target_size [ MB | GB | TB ]  } | DEFAULT ) ]   
    [ WITH NO_INFOMSGS ]   
[;]  
```  
  
## <a name="arguments"></a>引数  
SIZE = { *target_size* [ MB | **GB** | TB ]  } | **DEFAULT**.  
*target_size* は、DBCC SHRINKLOG が完了した後、すべての計算ノード全体のトランザクション ログの望ましいサイズです。 0 より大きい整数することをお勧めします。  
ログのサイズは、メガバイト (MB)、ギガバイト (GB)、またはテラバイト (TB) で測定されます。 すべてのコンピューティング ノードの上のトランザクション ログの合計サイズすることをお勧めします。  
既定では、DBCC SHRINKLOG がトランザクション ログをデータベースのメタデータに格納されているログのサイズに縮小されます。 メタデータのログ サイズは、[CREATE DATABASE &#40;Azure SQL Data Warehouse&#41;](../../t-sql/statements/create-database-azure-sql-data-warehouse.md) または [ALTER DATABASE &#40;Azure SQL Data Warehouse&#41;](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md) の LOG_SIZE パラメーターによって決まります。 DBCC SHRINKLOG は、`SIZE=DEFAULT` が指定されている場合、または `SIZE` 句が省略されている場合、トランザクション ログのサイズを既定サイズに縮小します。
  
WITH NO_INFOMSGS  
情報メッセージは、DBCC SHRINKLOG 結果には表示されません。  
  
## <a name="permissions"></a>アクセス許可  
ALTER SERVER STATE アクセス許可が必要です。
  
## <a name="general-remarks"></a>全般的な解説  
DBCC SHRINKLOG では、データベースのメタデータに格納されているログのサイズは変更されません。 CREATE DATABASE または ALTER DATABASE ステートメントで指定された LOG_SIZE パラメーターを格納するメタデータが続行します。
  
## <a name="examples"></a>使用例 
### <a name="a-shrink-the-transaction-log-to-the-original-size-specified-by-create-database"></a>A. トランザクション ログの圧縮 データベースの作成で指定された元のサイズにします。  
アドレスのデータベースが作成されたときに、アドレスのデータベースのトランザクション ログが 100 MB に設定があるとします。 つまり、アドレスの CREATE DATABASE ステートメントが LOG_SIZE 必要がある = 100 MB です。 ここで、150 MB、ログが大きくと、圧縮することを 100 MB にバックアップします。
  
次のステートメントの各については、アドレスのデータベースのトランザクション ログを 100 MB の既定のサイズに圧縮を試みます。 100 MB に、ログを圧縮すると、データ損失を引き起こす場合、DBCC SHRINKLOG はデータを失うことがなく、ログを 100 MB の場合より大きい最小サイズできるだけに縮小されます。
  
```sql
USE Addresses;  
DBCC SHRINKLOG ( SIZE = 100 MB );  
DBCC SHRINKLOG ( SIZE = DEFAULT );  
DBCC SHRINKLOG;  
```  
  
  
