---
title: ODBC の概要 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC]
- ODBC [ODBC], about ODBC
ms.assetid: 233315bd-2b7f-4b20-9978-e920e1ea9a07
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0a0515a882cd7d1c97a60e9262942bd7c397b0b2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298292"
---
# <a name="odbc-overview"></a>ODBC の概要
Open Database Connectivity (ODBC) は、データベース アクセスのために広く受け入れられているアプリケーション プログラミング インターフェイス (API) です。 これは、オープングループとデータベース API の ISO/IEC の呼び出しレベルインタフェース (CLI) 仕様に基づいており、データベース アクセス言語として構造化照会言語 (SQL) を使用します。  
  
 ODBC は、単一のアプリケーションが同じソース コードを使用して異なるデータベース管理システム (DBMS) にアクセスする機能*を最大限に*利用できるように設計されています。 データベース アプリケーションは *、ODBC*インターフェイスの関数を呼び出します。 ドライバーを使用すると、プリンター ドライバーがプリンター固有のコマンドからワード プロセッシング プログラムを分離するのと同じ方法で、データベース固有の呼び出しからアプリケーションを分離します。 ドライバーは実行時に読み込まれるため、ユーザーは新しい DBMS にアクセスするために新しいドライバーを追加するだけで済みます。アプリケーションを再コンパイルまたは再リンクする必要はありません。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ODBC の作成の目的](../../odbc/reference/why-was-odbc-created.md)  
  
-   [ODBC とは](../../odbc/reference/what-is-odbc.md)  
  
-   [ODBC と標準の CLI](../../odbc/reference/odbc-and-the-standard-cli.md)
