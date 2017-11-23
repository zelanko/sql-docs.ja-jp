---
title: "ODBC のテスト |Microsoft ドキュメント"
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
- ODBC test [ODBC]
- ODBC drivers [ODBC], testing
- gtrtst32.dll
- gtrts32w.dll [ODBC]
- odbct32w.exe [ODBC]
- odbcte32.exe [ODBC]
- testing ODBC drivers [ODBC]
ms.assetid: 7f13894c-5697-436c-be3d-fe16e1a02325
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 3db72d4424c197589f5b6f4ba07c54bf68070e9d
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="odbc-test"></a>ODBC のテスト
ODBC ドライバーと ODBC ドライバー マネージャーをテストに使用できる ODBC 対応のアプリケーションは、Microsoft® ODBC をテストします。 ODBC 3.51 には、ANSI と Unicode 対応のバージョンの ODBC のテストの両方が含まれています。 対応するファイルは次のとおりです。  
  
-   Odbcte32.exe と ANSI のバージョンについては、Gtrtst32.dll です。  
  
-   Odbct32w.exe と Unicode のバージョンについては、Gtrts32w.dll です。  
  
 ODBC のテストを使用するのには、ODBC API では、C 言語、および SQL を理解する必要があります。 ODBC API の詳細については、次を参照してください。、 [ODBC プログラマ リファレンス](../odbc/reference/odbc-programmer-s-reference.md)です。  
  
 以前のドキュメントのこのセクション内に含まれていたヘルプ トピックは、ODBC テスト プログラム内に含まれています。 Odbcte32.exe または Odbct32w.exe、開く開く、**ヘルプ** メニューをクリックして**ヘルプ トピック**です。  
  
 であっても、個別のファイル、32 ビット バージョンと同じ名前をこれらのアプリケーションは、64 ビット Microsoft Windows オペレーティング システム用の 64 ビット バージョンがあることに注意してください。 つまり ODBC テストの 64 ビット バージョンの Unicode バージョンの名前は、odbct32w.exe がします。
