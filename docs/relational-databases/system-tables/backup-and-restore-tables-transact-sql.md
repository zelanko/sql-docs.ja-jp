---
title: バックアップし、復元テーブル (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system tables [SQL Server], backup tables
- backup system tables [SQL Server]
- system tables [SQL Server], restore tables
- restore system tables [SQL Server]
ms.assetid: aa615add-54e6-40f5-8b55-3728b26884ee
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 021077a7e127f9c93ee752dea7f87aa12e792d02
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47596410"
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
  
  
