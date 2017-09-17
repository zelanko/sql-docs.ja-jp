---
title: "ブロック カーソルで使用するための列をバインド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- column-wise binding [ODBC]
- row-wise binding [ODBC]
- result sets [ODBC], binding columns
- cursors [ODBC], block
- binding columns [ODBC]
- block cursors [ODBC]
- result sets [ODBC], block cursors
ms.assetid: 231beede-cdfa-4e28-8b10-2760b983250f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fe8c88946d6602f77bc39ac03b280fcca99cb8de
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="binding-columns-for-use-with-block-cursors"></a>ブロック カーソルで使用するための列のバインド
ブロック カーソルは、複数の行を返す、ために、それらを使用するアプリケーションは、1 つの変数の代わりに、各列に変数の配列をバインドする必要があります。 これらの配列と総称されます、*行セット バッファー*です。 バインディングの 2 つのスタイルを次に示します。  
  
-   配列を各列にバインドします。 これと呼ばれる*列方向のバインド*各データ構造体 (配列) には、1 つの列のデータが含まれているためです。  
  
-   行全体のデータを保持し、これらの構造体の配列をバインドする構造体を定義します。 これと呼ばれる*行方向のバインド*データ構造ごとに 1 つの行のデータが含まれているためです。  
  
 アプリケーションは、列に 1 つの変数をバインドしたときに呼び出すよう**SQLBindCol**列に配列をバインドします。 唯一の違いは、渡されたアドレスに配列のアドレス、いない 1 つの変数のアドレスがあることです。 アプリケーションでは、列方向または行方向のバインドを使用しているかどうかを指定する SQL_BIND_BY_COLUMN ステートメント属性を設定します。 列方向または行方向のバインドを使用するかどうかは、大きくアプリケーション基本設定の問題です。 データのアプリケーションの配置より密接に対応する行方向のバインド、その場合、提供するパフォーマンスが向上します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [列方向のバインド](../../../odbc/reference/develop-app/column-wise-binding.md)  
  
-   [行方向のバインド](../../../odbc/reference/develop-app/row-wise-binding.md)
