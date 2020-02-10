---
title: external_languages (Transact-sql)-SQL Server |Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.reviewer: dphansen
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- external_languages
- external_languages_TSQL
- sys.external_languages
- sys.external_languages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_languages catalog view
author: nelgson
ms.author: negust
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1cef52f066a07032240d17f88297b02ba3f7e5fb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65995120"
---
# <a name="sysexternal_languages-transact-sql"></a>external_languages (Transact-sql)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

このカタログビューには、データベース内の外部言語の一覧が表示されます。 **R**と**Python**は予約された名前であり、これらの特定の名前を使用して外部言語を作成することはできません。

## <a name="sysexternal_languages"></a>sys.external_languages

カタログビューの external_languages には、データベース内の外部言語ごとに1行のデータが表示されます。

|列名 |データ型 | [説明]|
|------|------|------|
|external_language_id |INT | 外部言語の ID|
|言語 |sysname |外部言語の名前。 データベース内で一意です。 R と Python は、インスタンスごとに予約された名前です|
|create_date |datetime2 |作成日時|
|principal_id |INT |この外部ライブラリを所有するプリンシパルの ID|

## <a name="see-also"></a>参照  

+ [sys.external_language_files](sys-external-language-files-transact-sql.md)  
+ [外部言語の作成](../../t-sql/statements/create-external-language-transact-sql.md) 
