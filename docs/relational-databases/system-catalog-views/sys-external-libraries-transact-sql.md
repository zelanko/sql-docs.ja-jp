---
title: sys.external_libraries (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 10/05/2017
ms.prod: sql
ms.prod_service: database-engine
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
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 3f6d833488982da777d0f146d55f0a67fa945de5
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39553262"
---
# <a name="sysexternallibraries-transact-sql"></a>sys.external_libraries (TRANSACT-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]


R や Python などの外部のランタイムに関連するパッケージ ライブラリの管理をサポートしています。

## <a name="sysexternallibraries"></a>sys.external_libraries

カタログ ビューの sys.external_libraries には、データベースにアップロードされている外部ライブラリごとに 1 行が一覧表示します。

|列名 |データ型 | 説明|
|------|------|------|
|external_library_id |ssNoversion | 外部ライブラリ オブジェクトの ID。 |
|NAME |sysname |外部ライブラリの名前。 所有者ごとのデータベース内で一意です。|
|principal_id |ssNoversion |この外部ライブラリを所有するプリンシパルの ID。 |
|language | sysname | 言語または外部ライブラリをサポートするランタイムの名前。 有効な値は、'R' です。 追加のランタイムは、今後追加される可能性があります。|
|スコープ (scope) |ssNoversion |パブリック スコープ以外の場合は 0プライベート スコープ 1 |  
|scope_desc |varchar (7) |パッケージがパブリックかプライベートかどうかを示します|


## <a name="see-also"></a>参照  
[sys.external_library_files](sys-external-library-files-transact-sql.md)  
[外部ライブラリを作成します。](../../t-sql/statements/create-external-library-transact-sql.md)  
[SQL Server R Services のパッケージの管理](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
