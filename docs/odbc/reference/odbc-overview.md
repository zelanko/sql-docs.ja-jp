---
title: ODBC の概要 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6b064436dae6cb2f3d5f37fa02ab57a1e4a3f015
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63272927"
---
# <a name="odbc-overview"></a>ODBC の概要
Open Database Connectivity (ODBC) は、データベースへのアクセスに広く受け入れられているアプリケーション プログラミング インターフェイス (API) です。 データベース Api の Open Group および ISO/IEC からコールレベル インターフェイス (CLI) 仕様に基づいていて、そのデータベースへのアクセスの言語として構造化照会言語 (SQL) を使用します。  
  
 ODBC は、最大*相互運用性*のと同じソース コード管理システム (Dbms) 別のデータベースにアクセスする 1 つのアプリケーションの機能。 データベース アプリケーションと呼ばれるデータベース固有のモジュールで実装されている ODBC インターフェイスでの関数を呼び出す*ドライバー*します。 ドライバーの使用は、プリンター ドライバーがプリンター固有のコマンドからワード プロセッシング プログラムを分離することと同じ方法でデータベース固有の呼び出しからアプリケーションを分離します。 ユーザーが新しい DBMS; にアクセスする新しいドライバーを追加するだけが実行時に、ドライバーが読み込まれて、ため、場合によっては、再コンパイルやアプリケーションを再リンクする必要はありません。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ODBC の作成の目的](../../odbc/reference/why-was-odbc-created.md)  
  
-   [ODBC とは](../../odbc/reference/what-is-odbc.md)  
  
-   [ODBC と標準の CLI](../../odbc/reference/odbc-and-the-standard-cli.md)
