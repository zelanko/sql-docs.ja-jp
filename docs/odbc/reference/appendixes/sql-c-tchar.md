---
title: "SQL_C_TCHAR |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sql_c_tchar [ODBC]
- pseudo-type identifiers [ODBC], SQL_C_TCHAR
- data types [ODBC], pseudo-type identifiers
ms.assetid: 9e27c8bd-ee15-4ce9-b70a-34cf1bf16f4c
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 63c23a242b7acd7dd3cf10acb3f60dea980cd398
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlctchar"></a>SQL_C_TCHAR
SQL_C_TCHAR 型識別子が、データ型を実際には識別できません。これは、Unicode 変換用のヘッダー ファイル内に存在するマクロです。 UNICODE の設定に応じて SQL_C_CHAR または SQL_C_WCHAR によって置き換えられる**#define**です。 アプリケーションは、ANSI と Unicode のアプリケーションの両方としてコンパイルする文字データを転送するのに便利です。
