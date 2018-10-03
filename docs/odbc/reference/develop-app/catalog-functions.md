---
title: カタログ関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], about catalog functions
- data dictionary [ODBC]
- catalog functions [ODBC]
- functions [ODBC], catalog functions
ms.assetid: 81ba9453-c085-47c0-b411-90ca6a5ee428
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 268d5f00d787cef8dfdcb29bd9e091f81a5ed2c9
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47692170"
---
# <a name="catalog-functions"></a>カタログ関数
すべてのデータベースでは、データベース内のデータの格納方法が説明されている構造があります。 たとえば、単純な販売注文データベースには、リンク、テーブルに ID 列を使用する、次の図に示すように構造があります。  
  
 ![単純なデータベースの構造を示します](../../../odbc/reference/develop-app/media/pr19.gif "pr19")  
  
 特権などの他の情報と共に、この構造体が一連のデータベースのと呼ばれるシステム テーブルに格納されている*カタログ、* とも呼ばれますが、*データ ディクショナリ*します。  
  
 アプリケーションがこの構造体の呼び出しを通じてを検出、*カタログ関数*します。 カタログ関数を返す結果セットでの情報は通常を通じて実装**選択**カタログ内のテーブルに対してステートメントです。 たとえば、アプリケーションが、システム上のすべてのテーブルに関する情報を含む結果セット、または特定のテーブルが持つすべての列に関する情報を含む結果セットを要求するとします。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [カタログ データの使用](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
-   [ODBC のカタログ関数](../../../odbc/reference/develop-app/catalog-functions-in-odbc.md)
