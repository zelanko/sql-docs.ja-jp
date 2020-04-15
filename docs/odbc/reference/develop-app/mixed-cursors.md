---
title: 混合カーソル |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/20/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mixed cursors [ODBC]
- cursors [ODBC], dynamic
- keyset-driven cursors [ODBC]
- dynamic cursors [ODBC]
- cursors [ODBC], key-set driven
- cursors [ODBC], mixed
ms.assetid: 9beb2db9-0b6d-491d-9529-d64e64e59014
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a91dacf8ea9c0ed0db2c3b64634ddd53b854a534
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307437"
---
# <a name="mixed-cursors"></a>混合カーソル

混合カーソルは、キーセットドリブン カーソルと動的カーソルの組み合わせです。 結果セットが大きすぎて、結果セット全体のキーを適度に保存できなくなる場合に使用されます。 混合カーソルは、結果セット全体よりも小さいが行セットよりも大きいキーセットを作成することによって実装されます。  
  
 アプリケーションがキーセット内でスクロールする限り、動作はキーセット駆動です。 アプリケーションがキーセットの外側にスクロールすると、動作は動的になります: カーソルは要求された行をフェッチし、新しいキーセットを作成します。 新しいキーセットが作成されると、そのキーセット内で動作がキーセットドリブンに戻ります。  
  
 たとえば、結果セットに 1,000 行があり、キーセット サイズが 100、行セット サイズが 10 の混合カーソルを使用するとします。 最初の行セットがフェッチされると、カーソルは最初の 100 行のキーからなるキーセットを作成します。 要求に応じて、最初の 10 行を返します。  
  
 ここで、別のアプリケーションが行 11 と 101 を削除したとします。 カーソルが行 11 を取得しようとすると、この行のキーはあるが行が存在しないため、ギャップが発生します。これはキーセット駆動型の動作です。 カーソルが行 101 を検索しようとすると、カーソルは行のキーがないため、行が欠落していることを検出しません。 代わりに、前の行 102 を取得します。 これは動的カーソルの動作です。  
  
 キーセットのサイズが結果セットのサイズと等しい場合、混合カーソルはキーセットドリブン カーソルと同じです。 キーセットのサイズが 1 の場合、混合カーソルは動的カーソルと同じです。
