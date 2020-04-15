---
title: 結果の取得 (基本) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], about result sets
- data sources [ODBC], result sets
- empty result sets [ODBC]
ms.assetid: 052870e3-3f3f-4f07-91da-b649348225f4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3f7d01bf92fcee07940e449a2fb4bbac4f0fe6ac
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304333"
---
# <a name="retrieving-results-basic"></a>結果の取得 (基本)
*結果セット*は、特定の条件に一致するデータ ソースの行のセットです。 これは、クエリの結果として、アプリケーションが表形式で使用できる概念テーブルです。 **SELECT**ステートメント、カタログ関数、および一部のプロシージャーは、結果セットを作成します。 次の例では、最初の SQL ステートメントが Orders テーブルのすべての行とすべての列を含む結果セットを作成し、2 番目の SQL ステートメントは、ステータスが OPEN である受注テーブルの行に対して OrderID、SalesPerson、および Status 列を含む結果セットを作成します。  
  
```  
SELECT * FROM Orders  
SELECT OrderID, SalesPerson, Status FROM Orders WHERE Status = 'OPEN'  
```  
  
 結果セットは空にすることができますが、結果セットがない場合とは異なります。 たとえば、次の SQL ステートメントは空の結果セットを作成します。  
  
```  
SELECT * FROM Orders WHERE 1 = 2  
```  
  
 空の結果セットは、行がないことを除いて、他の結果セットと変わりません。 たとえば、アプリケーションは結果セットのメタデータを取得し、行をフェッチしようとし、結果セットの上にカーソルを閉じる必要があります。  
  
 データ ソースから行を取得し、それらをアプリケーションに返すプロセスを*fetching*と呼んでいます。 このセクションでは、そのプロセスの基本部分について説明します。 ブロックカーソルやスクロール可能なカーソルなど、より高度なトピックについては、「[ブロック カーソル](../../../odbc/reference/develop-app/block-cursors.md)と[スクロール可能なカーソル](../../../odbc/reference/develop-app/scrollable-cursors.md)」を参照してください。 行の更新、削除、および挿入については、「[データの更新の概要](../../../odbc/reference/develop-app/updating-data-overview.md)」を参照してください。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [結果セットは作成されましたか?](../../../odbc/reference/develop-app/was-a-result-set-created.md)  
  
-   [結果セットのメタデータ](../../../odbc/reference/develop-app/result-set-metadata.md)  
  
-   [バインディング列](../../../odbc/reference/develop-app/binding-columns.md)  
  
-   [データのフェッチ](../../../odbc/reference/develop-app/fetching-data.md)  
  
-   [カーソルを閉じる](../../../odbc/reference/develop-app/closing-the-cursor.md)
