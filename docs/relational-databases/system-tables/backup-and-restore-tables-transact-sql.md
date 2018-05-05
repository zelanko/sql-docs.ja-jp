---
title: バックアップし、復元テーブル (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system tables [SQL Server], backup tables
- backup system tables [SQL Server]
- system tables [SQL Server], restore tables
- restore system tables [SQL Server]
ms.assetid: aa615add-54e6-40f5-8b55-3728b26884ee
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: de2fb96afe4fb24cc7fe6455c880027d61d43ddb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="backup-and-restore-tables-transact-sql"></a>バックアップ テーブルと復元テーブル (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  ここでは、データベース バックアップと復元操作で使用される情報を格納するシステム テーブルについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [backupfile](../../relational-databases/system-tables/backupfile-transact-sql.md)  
 データベースの各データまたは各ログ ファイルに対して 1 行のデータを格納します。  
  
 [backupfilegroup](../../relational-databases/system-tables/backupfilegroup-transact-sql.md)  
 バックアップ時に、データベース内のファイル グループごとに 1 行のデータを格納します。  
  
 [backupmediafamily](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)  
 メディア ファミリごとに 1 行のデータを格納します。  
  
 [backupmediaset](../../relational-databases/system-tables/backupmediaset-transact-sql.md)  
 バックアップ メディア セットごとに 1 行のデータを格納します。  
  
 [backupset](../../relational-databases/system-tables/backupset-transact-sql.md)  
 バックアップ セットごとに 1 行のデータを格納します。  
  
 [logmarkhistory](../../relational-databases/system-tables/logmarkhistory-transact-sql.md)  
 コミットされたマーク付きのトランザクションごとに 1 行のデータを格納します。  
  
 [restorefile](../../relational-databases/system-tables/restorefile-transact-sql.md)  
 復元されたファイルごとに 1 行のデータを格納します。 これには、ファイル グループ名によって間接的に復元されたファイルが含まれます。  
  
 [restorefilegroup](../../relational-databases/system-tables/restorefilegroup-transact-sql.md)  
 復元されたファイル グループごとに 1 行のデータを格納します。  
  
 [restorehistory](../../relational-databases/system-tables/restorehistory-transact-sql.md)  
 復元操作ごとに 1 行のデータを格納します。  
  
 [suspect_pages](../../relational-databases/system-tables/suspect-pages-transact-sql.md)  
 824 エラーで失敗したページごとに 1 行のデータを格納します (最大 1,000 行)。  
  
 [sysopentapes](../../relational-databases/system-tables/sysopentapes-transact-sql.md)  
 現在開いているテープ デバイスごとに 1 行のデータを格納します。  
  
  
