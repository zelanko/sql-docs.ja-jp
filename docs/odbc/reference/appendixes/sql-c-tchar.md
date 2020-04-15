---
title: SQL_C_TCHAR |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 973d94b9b47371090a5f54fd3d259854ba78e9c2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304073"
---
# <a name="sql_c_tchar"></a>SQL_C_TCHAR
SQL_C_TCHAR型識別子は、実際にはデータ型を識別しません。これは、Unicode 変換用のヘッダー ファイル内に存在するマクロです。 UNICODE **#define**の設定に応じて、SQL_C_CHARまたはSQL_C_WCHARに置き換えられます。 これは、ANSI アプリケーションと Unicode アプリケーションの両方としてコンパイルされた文字データをアプリケーションが転送する場合に便利です。
