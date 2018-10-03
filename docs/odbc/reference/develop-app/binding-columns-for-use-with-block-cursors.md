---
title: ブロック カーソルで使用するための列の連結 |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c0ed819643e7ea818fc17c0fa317473afc8f5ca3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706380"
---
# <a name="binding-columns-for-use-with-block-cursors"></a>ブロック カーソルで使用するためのバインディング列
ブロック カーソルは、複数の行を返すため、それらを使用するアプリケーションは、1 つの変数ではなく、各列に変数の配列をバインドする必要があります。 これらのアレイと総称されます、*行セットのバッファー*します。 次に、バインディングの 2 つのスタイル。  
  
-   配列を各列にバインドします。 これは呼び出されます*列方向のバインド*各データ構造 (配列) には、1 つの列のデータが含まれています。  
  
-   行全体のデータを保持し、これらの構造体の配列をバインドする構造体を定義します。 これは呼び出されます*行方向のバインド*データ構造ごとに 1 つの行のデータが含まれています。  
  
 アプリケーションでは、1 つの変数が列にバインドしたときに呼び出されます**SQLBindCol**列に配列をバインドします。 唯一の違いは、渡されたアドレスは、配列のアドレス、いない 1 つの変数のアドレスであります。 アプリケーションでは、列方向または行方向のバインドが使用されているかどうかを指定する SQL_BIND_BY_COLUMN ステートメント属性を設定します。 列方向または行方向のバインドを使用するかどうかは、ほぼアプリケーションの基本設定の問題です。 データのアプリケーションのレイアウトに密接に対応する行方向のバインド、その場合、提供するパフォーマンスが向上します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [列方向のバインド](../../../odbc/reference/develop-app/column-wise-binding.md)  
  
-   [行方向のバインド](../../../odbc/reference/develop-app/row-wise-binding.md)
