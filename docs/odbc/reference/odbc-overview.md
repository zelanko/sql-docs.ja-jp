---
title: "ODBC の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC [ODBC]
- ODBC [ODBC], about ODBC
ms.assetid: 233315bd-2b7f-4b20-9978-e920e1ea9a07
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 20767544a83219c6583eaf03a78e240e15e19be2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-overview"></a>ODBC の概要
オープン データベース コネクティビティ (ODBC) は、データベース アクセスの広く受け入れられているアプリケーション プログラミング インターフェイス (API) です。 データベース Api のグループを開くと ISO/IEC から呼び出しレベル インターフェイス (CLI) 仕様に基づいていてには、データベース アクセスの言語として構造化照会言語 (SQL) を使用します。  
  
 ODBC は、最大*相互運用性*-別のデータベース管理システム (Dbms) を同じソース コードにアクセスする 1 つのアプリケーションの機能は、します。 データベース アプリケーションと呼ばれるデータベース固有のモジュールに実装されるインターフェイスで、ODBC 関数を呼び出す*ドライバー*です。 ドライバーの使用は、プリンター ドライバーがプリンター固有のコマンドからのワード プロセッシング プログラムを分離することと同じ方法でデータベースに固有の呼び出しからアプリケーションを分離します。 実行時に、ドライバーが読み込まれてため、ユーザーのみが新しい DBMS; にアクセスする新しいドライバーを追加するには再コンパイルやアプリケーションを再リンクする必要はありません。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ODBC が作成されたはなぜですか。](../../odbc/reference/why-was-odbc-created.md)  
  
-   [ODBC とは何ですか。](../../odbc/reference/what-is-odbc.md)  
  
-   [ODBC と標準の CLI](../../odbc/reference/odbc-and-the-standard-cli.md)

