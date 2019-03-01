---
title: sys.external_libraries (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 02/28/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- external_libraries
- external_libraries_TSQL
- sys.external_libraries
- sys.external_libraries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_libraries catalog view
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3a2f83d703566ae5a60fd027ff7f186205a0c404
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017538"
---
# <a name="sysexternallibraries-transact-sql"></a>sys.external_libraries (TRANSACT-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

R、Python、Java などの外部のランタイムに関連するパッケージ ライブラリの管理をサポートしています。

> [!NOTE]
> SQL Server 2017 での R 言語と Windows プラットフォームはサポートされています。 SQL Server 2019 CTP 2.3 では、R、Python、および Windows プラットフォーム上の Java がサポートされています。 Linux のサポートは今後のリリース予定です。

## <a name="sysexternallibraries"></a>sys.external_libraries

カタログ ビューの sys.external_libraries には、データベースにアップロードされている外部ライブラリごとに 1 行が一覧表示します。

|列名 |データ型 | 説明|
|------|------|------|
|external_library_id |ssNoversion | 外部ライブラリ オブジェクトの ID。 |
|NAME |sysname |外部ライブラリの名前。 所有者ごとのデータベース内で一意です。|
|principal_id |ssNoversion |この外部ライブラリを所有するプリンシパルの ID。 |
|language | sysname | 言語または外部ライブラリをサポートするランタイムの名前。 有効な値は、'R'、'Python' および 'Java' には。 追加のランタイムは、今後追加される可能性があります。|
|スコープ (scope) |ssNoversion |パブリック スコープ以外の場合は 0プライベート スコープ 1 |  
|scope_desc |varchar (7) |パッケージがパブリックかプライベートかどうかを示します|

## <a name="see-also"></a>関連項目  

+ [sys.external_library_files](sys-external-library-files-transact-sql.md)  
+ [外部ライブラリを作成します。](../../t-sql/statements/create-external-library-transact-sql.md)  
+ [SQL Server に新しい R パッケージをインストールする](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md)  
+ [SQL Server に新しい Python パッケージをインストールする](../../advanced-analytics/python/install-additional-python-packages-on-sql-server.md)  