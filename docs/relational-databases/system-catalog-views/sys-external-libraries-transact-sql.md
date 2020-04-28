---
title: external_libraries (Transact-sql) |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "80664430"
---
# <a name="sysexternal_libraries-transact-sql"></a>sys.external_libraries (Transact-SQL)  
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

では、R、Python、Java などの外部ランタイムに関連するパッケージライブラリの管理がサポートされています。

> [!NOTE]
> SQL Server 2017 では、R 言語と Windows プラットフォームがサポートされています。 Windows および Linux プラットフォームの R、Python、Java は SQL Server 2019 以降でサポートされています。

## <a name="sysexternal_libraries"></a>sys.external_libraries

カタログビューの external_libraries には、データベースにアップロードされた各外部ライブラリの行が一覧表示されます。

|列名 |データ型 | 説明|
|------|------|------|
|external_library_id |int | 外部ライブラリオブジェクトの ID。 |
|name |sysname |外部ライブラリの名前。 所有者ごとにデータベース内で一意です。|
|principal_id |int |この外部ライブラリを所有するプリンシパルの ID。 |
|language | sysname | 外部ライブラリをサポートする言語またはランタイムの名前。 有効な値は、' R '、' Python '、および ' Java ' です。 今後、追加のランタイムが追加される可能性があります。|
|scope |int |パブリックスコープの場合は0。プライベートスコープの場合は1 |  
|scope_desc |varchar (7) |パッケージがパブリックであるかプライベートであるかを示します|

## <a name="see-also"></a>関連項目  

+ [sys.external_library_files](sys-external-library-files-transact-sql.md)  
+ [外部ライブラリの作成](../../t-sql/statements/create-external-library-transact-sql.md)  
+ [SQL Server に新しい R パッケージをインストールする](../../machine-learning/package-management/install-additional-r-packages-on-sql-server.md)  
+ [SQL Server に新しい Python パッケージをインストールする](../../machine-learning/package-management/install-additional-python-packages-on-sql-server.md)  