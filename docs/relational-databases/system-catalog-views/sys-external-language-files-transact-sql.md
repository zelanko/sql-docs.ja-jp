---
title: external_language_files (Transact-sql)-SQL Server |Microsoft Docs
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
ms.openlocfilehash: 0d1325311ef0b708f5a3abd5f4494e099863efc2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "65995090"
---
# <a name="sysexternal_language_files-transact-sql"></a>external_language_files (Transact-sql)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

このカタログビューには、データベース内の外部言語拡張ファイルの一覧が表示されます。 **R**と**Python**は予約された名前であり、これらの特定の名前を使用して外部言語を作成することはできません。

File_spec から外部言語が作成されると、拡張機能自体とそのプロパティがこのビューに表示されます。 このビューには、OS ごとに1つのエントリが含まれます。

## <a name="sysexternal_languages"></a>sys.external_languages

カタログビューの external_language_files には、データベース内の外部言語拡張機能ごとに1行のデータが表示されます。 パラメーター

|列名 |データ型 | [説明]|
|------|------|------|
|external_language_id |INT | 外部言語の ID|
|content|varbinary(max) |外部言語拡張ファイルの内容|
|file_name|nvarchar (266)|言語拡張ファイルの名前|
|プラットフォーム|tinyint|SQL Server がインストールされているホストプラットフォームの ID|
|platform_desc |nvarchar(60)|ホストプラットフォームの名前。 有効な値は ' WINDOWS '、' LINUX ' です。|
|parameters|nvarchar(4000)|外部言語 prameters|
|environment_variables |nvarchar(4000)|外部言語環境変数|

## <a name="see-also"></a>参照  

+ [sys.external_languages](sys-external-languages-transact-sql.md)  
+ [外部言語の作成](../../t-sql/statements/create-external-language-transact-sql.md)  
