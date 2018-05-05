---
title: 既定の C データ型 |Microsoft ドキュメント
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
- data types [ODBC], pseudo-type identifiers
- pseudo-type identifiers [ODBC], about pseudo-type identifiers
- pseudo-type identifiers [ODBC]
ms.assetid: 229140ae-af8f-4ec8-9ccf-1e92360e0bac
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ec05e58cd651497b07e131d4c3dcfe2e70baa04f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="default-c-data-types"></a>既定の C データ型
アプリケーションで SQL_C_DEFAULT を指定する場合**SQLBindCol**、 **SQLGetData**、または**SQLBindParameter**ドライバーは、その出力、入力バッファーの C データ型が前提としています。列またはパラメーターのバッファーのバインド先の SQL データ型に対応します。  
  
> [!IMPORTANT]  
>  相互運用可能アプリケーションは SQL_C_DEFAULT を使用しないでください。 代わりを使用するバッファーの C 型を必ず指定する必要があります。 これは、ドライバーが次の理由で既定の C 型を常に正しく判断できないためにです。  
  
-   DBMS プロモート、SQL データ型の列またはパラメーターの場合、ドライバーは、元の SQL データ型の列またはパラメーターを特定できません。 そのため、対応する既定の C データ型がわかりません。  
  
-   ドライバーを特定できない場合、特定の列またはパラメーターが署名されているか、同様に、多くの場合、これが、ドライバーが判断できない、DBMS によって処理される対応する既定の C データを入力するかどうか必要があります署名または署名されていません。  
  
     SQL_C_DEFAULT はプログラミングの利便性としてのみ提供される、ため、アプリケーションが実際の C データ型を指定する場合の機能をすべてを失うしていません。  
  
 各 SQL データ型の既定の C データ型を示すテーブルが含まれている[に変換するデータを SQL から C データ型に](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)、後の「します。
