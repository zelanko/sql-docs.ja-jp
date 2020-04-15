---
title: 既定の C データ型 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], pseudo-type identifiers
- pseudo-type identifiers [ODBC], about pseudo-type identifiers
- pseudo-type identifiers [ODBC]
ms.assetid: 229140ae-af8f-4ec8-9ccf-1e92360e0bac
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fdb787580e1c79df805f468416ab8993a1d32a26
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307053"
---
# <a name="default-c-data-types"></a>既定の C データ型
アプリケーションが**SQLBindCol** **、SQLGetData**、または**SQLBindParameter**でSQL_C_DEFAULTを指定した場合、ドライバーは、出力バッファーまたは入力バッファーの C データ型が、バッファーがバインドされている列またはパラメーターの SQL データ型に対応すると想定します。  
  
> [!IMPORTANT]  
>  相互運用可能なアプリケーションでは、SQL_C_DEFAULTを使用しないでください。 代わりに、使用するバッファの C 型を常に指定する必要があります。 これは、次の理由により、ドライバーが常に既定の C 型を正しく判断できないためです。  
  
-   DBMS が列またはパラメーターの SQL データ型を昇格させる場合、ドライバーは、列またはパラメーターの元の SQL データ型を決定できません。 したがって、対応するデフォルト C データ型を判別することはできません。  
  
-   特定の列またはパラメーターが署名されているかどうかをドライバーが判断できない場合は、DBMS によって処理される場合が多い場合、ドライバーは、対応する既定の C データ型が署名または署名されていないかどうかを判断できません。  
  
     SQL_C_DEFAULTはプログラミングの利便性のためだけに提供されるため、実際の C データ型を指定しても、アプリケーションは機能を失いません。  
  
 各 SQL データ型の既定の C データ型を示す表は、この付録の後半の[「SQL から C データ型へのデータの変換](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)」に記載されています。
