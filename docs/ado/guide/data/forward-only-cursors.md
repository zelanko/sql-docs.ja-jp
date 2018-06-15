---
title: 順方向専用カーソル |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], forward-only
- forward-only cursors [ADO]
ms.assetid: 2b1e062f-3294-4a6f-8241-a17045c4df18
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8a309a34d8b5a897c62de6bdceb1db2eef4d46c2
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35271481"
---
# <a name="forward-only-cursors"></a>順方向専用カーソル
順方向専用 (またはスクロールできない) のカーソルと呼ばれる代表的な既定カーソルの種類は、結果セットを前方に移動できます。 順方向専用カーソルがスクロール (結果セットに前方と後方に移動する機能) をサポートしていませんまた、先頭から、結果セットの末尾に行をフェッチのみサポートされます。 いくつか順方向専用カーソルで (など、SQL Server カーソル ライブラリで)、すべて insert、update、および delete ステートメントの現在のユーザーによって行われた (またはその他のユーザーによってコミットされる)、結果セットの行に影響を表示しているように、行をフェッチすることです。 カーソルを後方にスクロールすることはできません、ためただし、行のフェッチ後に、データベース内の行に加えられた変更は、カーソルによっては表示されません。  
  
 現在の行のデータが処理されると、順方向専用カーソルは、そのデータを保持するために使用されたリソースを解放します。 順方向専用カーソルは、既定では、現在の行が処理されると、すべての変更が検出されたことを意味動的です。 これにより、高速なカーソルのオープンを提供し、結果セットを基になるテーブルに加えられた更新プログラムを表示します。  
  
 順方向専用カーソルは、後方スクロールをサポートしていない、ときに、アプリケーションを閉じると、カーソルを閉じて、結果セットの先頭に戻ります。 これは、少量のデータを操作する効果的な方法です。 アプリケーションが、結果セットを 1 回読み取りでした代わりには、データをローカルにキャッシュし、ローカル データ キャッシュを参照します。  
  
 場合は、アプリケーションでは、結果セットをスクロールすることは不要、順方向専用カーソルは、最小限のオーバーヘッドで迅速にデータを取得する最適な方法です。 使用して、 **adOpenForwardOnly CursorTypeEnum** ADO では順方向専用カーソルを使用することを示すためにします。  
  
## <a name="see-also"></a>参照  
 [静的カーソル](../../../ado/guide/data/static-cursors.md)   
 [Keyset カーソル](../../../ado/guide/data/keyset-cursors.md)   
 [動的カーソル](../../../ado/guide/data/dynamic-cursors.md)
