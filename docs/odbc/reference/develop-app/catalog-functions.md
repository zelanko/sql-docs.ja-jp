---
title: カタログ関数 |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305203"
---
# <a name="catalog-functions"></a>カタログ関数
すべてのデータベースには、データベースにデータを格納する方法を示す構造があります。 たとえば、単純な販売注文データベースの構造を次の図に示します。  
  
 ![単純なデータベースの構造の表示](../../../odbc/reference/develop-app/media/pr19.gif "pr19")  
  
 この構造体は、特権などの他の情報と共に、データベースの*カタログ*と呼ばれるシステム テーブルのセットに格納*されます。*  
  
 アプリケーションは、*カタログ関数*の呼び出しを通じてこの構造を検出できます。 カタログ関数は結果セット内の情報を返し、通常はカタログ内のテーブルに対して**SELECT**ステートメントを使用して実装されます。 たとえば、アプリケーションが、システム上のすべてのテーブルに関する情報を含む結果セット、または特定のテーブルが持つすべての列に関する情報を含む結果セットを要求するとします。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [カタログ データの使用](../../../odbc/reference/develop-app/uses-of-catalog-data.md)  
  
-   [ODBC のカタログ関数](../../../odbc/reference/develop-app/catalog-functions-in-odbc.md)
