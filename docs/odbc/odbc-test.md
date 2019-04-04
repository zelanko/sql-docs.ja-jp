---
title: ODBC のテスト |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC test [ODBC]
- ODBC drivers [ODBC], testing
- gtrtst32.dll
- gtrts32w.dll [ODBC]
- odbct32w.exe [ODBC]
- odbcte32.exe [ODBC]
- testing ODBC drivers [ODBC]
ms.assetid: 7f13894c-5697-436c-be3d-fe16e1a02325
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 797f572a6a9d847422981483c4bfe7938cd47e50
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626190"
---
# <a name="odbc-test"></a>ODBC のテスト
Microsoft® ODBC のテストは、ODBC ドライバーと ODBC ドライバー マネージャーのテストに使用できる ODBC 対応のアプリケーションです。 ODBC 3.51 には、ANSI および Unicode 対応のバージョンの ODBC のテストの両方が含まれています。 対応するファイルは次のとおりです。  
  
-   Odbcte32.exe と ANSI のバージョンについては、Gtrtst32.dll します。  
  
-   Odbct32w.exe と Unicode のバージョンについては、Gtrts32w.dll します。  
  
 ODBC のテストを使用するには、ODBC API では、C 言語、および SQL を理解する必要があります。 ODBC API の詳細については、、 [ODBC プログラマ リファレンス](../odbc/reference/odbc-programmer-s-reference.md)を参照してください。  
  
 以前のドキュメントのこのセクション内に含まれていたヘルプ トピックは ODBC テスト プログラム内に含まれています。 開く Odbcte32.exe または Odbct32w.exe、オープン、**ヘルプ** メニューをクリック**ヘルプ トピック**します。  
  
 個別のファイルがあるにもかかわらず、32 ビット バージョンのと同じ名前をこれらのアプリケーションは、64 ビット Microsoft Windows オペレーティング システムでは、目的の 64 ビット バージョンがあることに注意してください。 つまり、という名前の ODBC のテストの 64 ビット バージョンの Unicode バージョン odbct32w.exe
