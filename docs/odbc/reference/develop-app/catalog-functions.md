---
title: カタログ関数 |Microsoft ドキュメント
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
- catalog functions [ODBC], about catalog functions
- data dictionary [ODBC]
- catalog functions [ODBC]
- functions [ODBC], catalog functions
ms.assetid: 81ba9453-c085-47c0-b411-90ca6a5ee428
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 582b6d0912263d2eba76a7e357787c7c75ba0a75
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="catalog-functions"></a>カタログ関数
すべてのデータベースは、データベース内のデータの格納方法が説明されている構造を持っています。 たとえば、販売注文の単純なデータベースには、テーブルをリンクする、ID 列を使用する、次の図に示すように構造体があります。  
  
 ![単純なデータベースの構造を示します](../../../odbc/reference/develop-app/media/pr19.gif "pr19")  
  
 特権などの他の情報と共に、この構造体が、データベースと呼ばれるシステム テーブルのセットに格納されている*カタログ、*とも呼ばれますが、*データ辞書*です。  
  
 アプリケーションは、この構造体への呼び出しを通してを検出できる、*カタログ関数*です。 カタログ関数を返す結果セットでの情報は、通常を介して実装**選択**カタログ内のテーブルに対してステートメントです。 たとえば、アプリケーションが、システム上のすべてのテーブルに関する情報を含む結果セット、または特定のテーブルが持つすべての列に関する情報を含む結果セットを要求するとします。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [カタログ データの使用](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
-   [ODBC のカタログ関数](../../../odbc/reference/develop-app/catalog-functions-in-odbc.md)
