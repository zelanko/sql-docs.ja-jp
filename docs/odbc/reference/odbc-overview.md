---
title: ODBC の概要 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC]
- ODBC [ODBC], about ODBC
ms.assetid: 233315bd-2b7f-4b20-9978-e920e1ea9a07
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e1d296b9780d520beb6e5ddd52f60cf27b05fe1f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-overview"></a>ODBC の概要
オープン データベース コネクティビティ (ODBC) は、データベース アクセスの広く受け入れられているアプリケーション プログラミング インターフェイス (API) です。 データベース Api のグループを開くと ISO/IEC から呼び出しレベル インターフェイス (CLI) 仕様に基づいていてには、データベース アクセスの言語として構造化照会言語 (SQL) を使用します。  
  
 ODBC は、最大*相互運用性*-別のデータベース管理システム (Dbms) を同じソース コードにアクセスする 1 つのアプリケーションの機能は、します。 データベース アプリケーションと呼ばれるデータベース固有のモジュールに実装されるインターフェイスで、ODBC 関数を呼び出す*ドライバー*です。 ドライバーの使用は、プリンター ドライバーがプリンター固有のコマンドからのワード プロセッシング プログラムを分離することと同じ方法でデータベースに固有の呼び出しからアプリケーションを分離します。 実行時に、ドライバーが読み込まれてため、ユーザーのみが新しい DBMS; にアクセスする新しいドライバーを追加するには再コンパイルやアプリケーションを再リンクする必要はありません。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ODBC の作成の目的](../../odbc/reference/why-was-odbc-created.md)  
  
-   [ODBC とは](../../odbc/reference/what-is-odbc.md)  
  
-   [ODBC と標準の CLI](../../odbc/reference/odbc-and-the-standard-cli.md)
