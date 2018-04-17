---
title: sys.external_libraries (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 10/05/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
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
author: jeannt
ms.author: jeannt
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: d8fa8a4d41cff452379c420b712f13b2d4415a74
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysexternallibraries-transact-sql"></a>sys.external_libraries (TRANSACT-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]


R、Python などの外部のランタイムに関連するパッケージ ライブラリの管理をサポートします。

## <a name="sysexternallibraries"></a>sys.external_libraries

カタログ ビュー sys.external_libraries には、データベースにアップロードされている外部ライブラリごとに行が一覧表示します。

|列名 |データ型 | Description|
|------|------|------|
|external_library_id |int | 外部ライブラリ オブジェクトの ID。 |
|name |sysname |外部ライブラリの名前です。 所有者ごとのデータベース内で一意です。|
|principal_id |int |この外部ライブラリを所有するプリンシパルの ID です。 |
|language | sysname | 言語または外部のライブラリをサポートするランタイムの名前。 有効な値は、'R' です。 追加のランタイムは、将来追加される可能性があります。|
|スコープ (scope) |int |パブリックのスコープ以外の場合は 0プライベート スコープの場合は 1 |  
|scope_desc |varchar (7) |パッケージがパブリックかプライベートかどうかを示します|


## <a name="see-also"></a>参照  
[sys.external_library_files](sys-external-library-files-transact-sql.md)  
[外部ライブラリを作成します。](../../t-sql/statements/create-external-library-transact-sql.md)  
[SQL Server R Services のパッケージの管理](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
