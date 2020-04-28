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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eb28ec6f4ea299dae8737fc707fd53e4d102442d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305203"
---
# <a name="catalog-functions"></a>カタログ関数
すべてのデータベースには、データをデータベースに格納する方法を示す構造があります。 たとえば、単純な販売注文データベースには、次の図に示す構造があります。ここでは、ID 列を使用してテーブルをリンクします。  
  
 ![単純なデータベースの構造の表示](../../../odbc/reference/develop-app/media/pr19.gif "pr19")  
  
 この構造は、特権などの他の情報と共に、データベースの*カタログ*と呼ばれる一連のシステムテーブルに格納されます。これは、*データ辞書*とも呼ばれます。  
  
 アプリケーションは、*カタログ関数*の呼び出しによってこの構造を検出できます。 カタログ関数は、結果セットの情報を返します。通常は、カタログ内のテーブルに対して**SELECT ステートメントを**使用して実装されます。 たとえば、アプリケーションが、システム上のすべてのテーブルに関する情報を含む結果セット、または特定のテーブルが持つすべての列に関する情報を含む結果セットを要求するとします。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [カタログ データの使用](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
-   [ODBC のカタログ関数](../../../odbc/reference/develop-app/catalog-functions-in-odbc.md)
