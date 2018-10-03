---
title: カーソルを混合 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1905bc30afff4af0ffc74363b93f95732f4760f1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47631760"
---
# <a name="mixed-cursors"></a>混合カーソル
混合カーソル、キーセット ドリブン カーソルと動的カーソルの組み合わせです。 結果セットが大きすぎて、ある程度結果セット全体のキーを保存時に使用されます。 混合カーソルを実装するには、全体の結果セットよりも小さい行セットよりも大きいキーセットを作成します。  
  
 アプリケーションは、キーセット内でスクロールする限り動作は、キーセット ドリブンです。 動作は動的で、アプリケーションによってキーセット外にスクロールします。 カーソルが要求された行をフェッチし、新しいキーセットを作成します。 新しいキーセットを作成した後、動作は、そのキーセット内でキーセット ドリブンに戻ります。  
  
 たとえば、結果セットが 1,000 行と 100 のキーセットのサイズと 10 の行セット サイズの混合カーソルを使用します。 最初の行セットをフェッチするとき、カーソルは、最初の 100 行のキーから成るキーセットを作成します。 要求に応じてその後、最初の 10 個の行を返します。  
  
 もう 1 つのアプリケーションの削除行 11 と 101 ものとします。 この行のキーを持つ行が存在しないためがの場合は、カーソルが 11 の行を取得しようとすると、穴を発生します。これは、キーセット ドリブンの動作です。 カーソルは、101 行目を取得しようとすると、カーソルには、行のキーがあるないため、行が不足していることは検出されません。 代わりに、行 102 していたが取得されます。 これは、動的カーソルの動作です。  
  
 キーセットのサイズが、結果セットのサイズに等しい場合に、混合カーソルはキーセット ドリブン カーソルと同じです。 混合カーソルは、キーセットのサイズが 1 に等しい場合に、動的カーソルと同じです。
