---
title: ODBC の概要 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
ms.openlocfilehash: 39ab7586ebc1cd63d028caab0d3c2f09b82c7172
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32916077"
---
# <a name="odbc-overview"></a>ODBC の概要
オープン データベース コネクティビティ (ODBC) は、データベース アクセスの広く受け入れられているアプリケーション プログラミング インターフェイス (API) です。 データベース Api のグループを開くと ISO/IEC から呼び出しレベル インターフェイス (CLI) 仕様に基づいていてには、データベース アクセスの言語として構造化照会言語 (SQL) を使用します。  
  
 ODBC は、最大*相互運用性*-別のデータベース管理システム (Dbms) を同じソース コードにアクセスする 1 つのアプリケーションの機能は、します。 データベース アプリケーションと呼ばれるデータベース固有のモジュールに実装されるインターフェイスで、ODBC 関数を呼び出す*ドライバー*です。 ドライバーの使用は、プリンター ドライバーがプリンター固有のコマンドからのワード プロセッシング プログラムを分離することと同じ方法でデータベースに固有の呼び出しからアプリケーションを分離します。 実行時に、ドライバーが読み込まれてため、ユーザーのみが新しい DBMS; にアクセスする新しいドライバーを追加するには再コンパイルやアプリケーションを再リンクする必要はありません。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ODBC の作成の目的](../../odbc/reference/why-was-odbc-created.md)  
  
-   [ODBC とは](../../odbc/reference/what-is-odbc.md)  
  
-   [ODBC と標準の CLI](../../odbc/reference/odbc-and-the-standard-cli.md)
