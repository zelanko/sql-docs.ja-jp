---
title: 識別子ケース |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- identifiers [ODBC], case
- interoperability of SQL statements [ODBC], identifier case
ms.assetid: ee8a31aa-389d-4dd1-bfa9-547f6b50bc70
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 940d96ece6b2c344fa02e0daadd6248270f4d19e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300152"
---
# <a name="identifier-case"></a>識別子の大文字と小文字の区別
SQL ステートメントおよびカタログ関数の引数では、識別子と引用符で囲まれた識別子は大文字と小文字を区別する場合でも、大文字と小文字を区別する場合でも、アプリケーションは SQL_IDENTIFIER_CASE オプションとSQL_QUOTED_IDENTIFIER_CASE オプションを指定して**SQLGetInfo**を呼び出して判断できます。  
  
 これらの各オプションには、識別子または引用符で囲まれた識別子の大文字と小文字が区別され、3 つは区別されないことを示す 4 つの戻り値があります。 大文字と小文字を区別しない 3 つの値は、システム・カタログに ID が保管される場合をさらに詳しく説明します。 システムカタログに識別子を格納する方法は、アプリケーションがカタログ機能の結果を表示する場合など、表示目的にのみ関連します。識別子の大文字と小文字の区別は変更されません。
