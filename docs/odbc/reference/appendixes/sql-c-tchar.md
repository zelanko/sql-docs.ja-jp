---
title: SQL_C_TCHAR |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- sql_c_tchar [ODBC]
- pseudo-type identifiers [ODBC], SQL_C_TCHAR
- data types [ODBC], pseudo-type identifiers
ms.assetid: 9e27c8bd-ee15-4ce9-b70a-34cf1bf16f4c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 42afb911dda26cbda53f9cd14c883abb3775b94b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63270524"
---
# <a name="sqlctchar"></a>SQL_C_TCHAR
SQL_C_TCHAR 型識別子が、データ型を実際に識別できません。これは、Unicode への変換用のヘッダー ファイル内に存在するマクロです。 UNICODE の設定に応じて SQL_C_CHAR、SQL_C_WCHAR またはによって置き換えられる **#define**します。 ANSI および Unicode アプリケーションの両方としてコンパイルされる文字データを転送するアプリケーションに適しています。
