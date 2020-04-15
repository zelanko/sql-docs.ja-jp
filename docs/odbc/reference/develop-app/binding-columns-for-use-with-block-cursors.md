---
title: ブロックカーソルで使用する列のバインド |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- column-wise binding [ODBC]
- row-wise binding [ODBC]
- result sets [ODBC], binding columns
- cursors [ODBC], block
- binding columns [ODBC]
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 231beede-cdfa-4e28-8b10-2760b983250f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bc7e527658a7d6945921510de898c648075c41fc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284902"
---
# <a name="binding-columns-for-use-with-block-cursors"></a>ブロック カーソルで使用するためのバインディング列
ブロック カーソルは複数の行を返すため、それらを使用するアプリケーションは、変数の配列を 1 つの変数ではなく、各列にバインドする必要があります。 これらの配列は、まとめて*行セット バッファー*と呼ばれます。 次に、2 つのスタイルのバインドを示します。  
  
-   配列を各列にバインドします。 各データ構造 (配列) には単一*列の*データが含まれているため、列方向のバインドと呼ばれます。  
  
-   行全体のデータを保持する構造体を定義し、これらの構造体の配列をバインドします。 各データ構造には 1 つの行のデータが含まれているため、これは*行方向のバインド*と呼ばれます。  
  
 アプリケーションは、単一の変数を列にバインドするときと同様に **、SQLBindCol**を呼び出して配列を列にバインドします。 唯一の違いは、渡されるアドレスは配列アドレスであり、単一の変数アドレスではないということです。 アプリケーションは、SQL_BIND_BY_COLUMNステートメント属性を設定して、それが列方向または行方向のバインディングを使用するかどうかを指定します。 列方向バインディングと行方向バインディングのどちらを使用するかは、アプリケーションの好みの問題です。 行方向のバインドは、アプリケーションのデータのレイアウトにより密接に対応する可能性があり、その場合はパフォーマンスが向上します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [列方向のバインド](../../../odbc/reference/develop-app/column-wise-binding.md)  
  
-   [行方向のバインド](../../../odbc/reference/develop-app/row-wise-binding.md)
