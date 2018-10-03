---
title: sys.external_libraries (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 10/05/2017
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
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 19704a37c9f34ee3b27bdee962246d98c0b18e71
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47796620"
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


## <a name="see-also"></a>関連項目  
[sys.external_library_files](sys-external-library-files-transact-sql.md)  
[外部ライブラリを作成します。](../../t-sql/statements/create-external-library-transact-sql.md)  
[SQL Server R Services のパッケージの管理](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
