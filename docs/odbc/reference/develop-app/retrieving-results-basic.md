---
title: 結果 (基本) を取得する |Microsoft ドキュメント
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
- result sets [ODBC], about result sets
- data sources [ODBC], result sets
- empty result sets [ODBC]
ms.assetid: 052870e3-3f3f-4f07-91da-b649348225f4
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b09820c0716d6d7a8261ede3b5a4173dc73f384d
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="retrieving-results-basic"></a>結果 (基本) を取得します。
A*結果セット*特定の条件に一致するデータ ソース上の行のセットです。 これは、クエリの実行結果し、するアプリケーションが使用できる、表形式で概念テーブルです。 **選択**ステートメント、カタログ関数、およびいくつかの手順は、結果セットを作成します。 次の例では、最初の SQL ステートメントは、すべての行と Orders テーブル内のすべての列を含む結果セットを作成し、2 番目の SQL ステートメントの Orders テーブル内の行の OrderID、販売員、およびステータスの列を含む結果セットを作成します。状態の開く。  
  
```  
SELECT * FROM Orders  
SELECT OrderID, SalesPerson, Status FROM Orders WHERE Status = 'OPEN'  
```  
  
 結果セットとは何の結果もすべての設定に異なる、空で指定できます。 たとえば、次の SQL ステートメントには、空の結果セットを作成します。  
  
```  
SELECT * FROM Orders WHERE 1 = 2  
```  
  
 空の結果セットは、その他の結果セットから行を持たないする点を除いて同じです。 たとえば、アプリケーション結果セットのメタデータを取得することができます、行をフェッチしようとしてでき、結果セットに対して、カーソルを閉じる必要があります。  
  
 データ ソースから行を取得して、それらをアプリケーションに返すのプロセスが呼び出されると*フェッチ*です。 このセクションでは、そのプロセスの基本的な構成要素について説明します。 スクロール可能なカーソルは、ブロックなどのより高度なトピックについての情報を参照してください。[ブロック カーソル](../../../odbc/reference/develop-app/block-cursors.md)と[スクロール可能なカーソル](../../../odbc/reference/develop-app/scrollable-cursors.md)です。 更新については、削除、および行の挿入を参照してください[更新データの概要](../../../odbc/reference/develop-app/updating-data-overview.md)です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [結果セットは作成されましたか?](../../../odbc/reference/develop-app/was-a-result-set-created.md)  
  
-   [結果セットのメタデータ](../../../odbc/reference/develop-app/result-set-metadata.md)  
  
-   [バインディング列](../../../odbc/reference/develop-app/binding-columns.md)  
  
-   [データのフェッチ](../../../odbc/reference/develop-app/fetching-data.md)  
  
-   [カーソルを閉じる](../../../odbc/reference/develop-app/closing-the-cursor.md)
