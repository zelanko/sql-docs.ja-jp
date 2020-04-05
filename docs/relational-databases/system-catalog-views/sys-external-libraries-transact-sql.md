---
title: external_libraries (トランザクション-SQL) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: machine-learning
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
ms.openlocfilehash: 6b1bfc00b403fa76f692db78593ed4c0e6b53ce8
ms.sourcegitcommit: 68583d986ff5539fed73eacb7b2586a71c37b1fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2020
ms.locfileid: "80664430"
---
# <a name="sysexternal_libraries-transact-sql"></a>sys.external_libraries (Transact-SQL)  
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

R、Python、Java などの外部ランタイムに関連するパッケージライブラリの管理をサポートします。

> [!NOTE]
> SQL Server 2017 では、R 言語と Windows プラットフォームがサポートされています。 Windows および Linux プラットフォームの R、Python、Java は SQL Server 2019 以降でサポートされています。

## <a name="sysexternal_libraries"></a>sys.external_libraries

カタログ ビュー sys.external_libraries には、データベースにアップロードされた各外部ライブラリの行が一覧表示されます。

|列名 |データ型 | 説明|
|------|------|------|
|external_library_id |INT | 外部ライブラリ オブジェクトの ID。 |
|name |sysname |外部ライブラリの名前。 所有者ごとにデータベース内で一意です。|
|principal_id |INT |この外部ライブラリを所有するプリンシパルの ID。 |
|language | sysname | 外部ライブラリをサポートする言語またはランタイムの名前。 有効な値は'R'、'Python'、および'Java'です。 今後、ランタイムが追加される可能性があります。|
|scope |INT |パブリック スコープの場合は 0。プライベート スコープの場合は 1 |  
|scope_desc |ヴァルチャー(7) |パッケージがパブリックかプライベートかを示します。|

## <a name="see-also"></a>関連項目  

+ [sys.external_library_files](sys-external-library-files-transact-sql.md)  
+ [外部ライブラリの作成](../../t-sql/statements/create-external-library-transact-sql.md)  
+ [SQL Server に新しい R パッケージをインストールする](../../machine-learning/package-management/install-additional-r-packages-on-sql-server.md)  
+ [SQL Server に新しい Python パッケージをインストールする](../../machine-learning/package-management/install-additional-python-packages-on-sql-server.md)  