---
title: カーソルを混合 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- mixed cursors [ODBC]
- cursors [ODBC], dynamic
- keyset-driven cursors [ODBC]
- dynamic cursors [ODBC]
- cursors [ODBC], key-set driven
- cursors [ODBC], mixed
ms.assetid: 9beb2db9-0b6d-491d-9529-d64e64e59014
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 27038553bb380c67f66d8137354d7cbec4ff1a33
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="mixed-cursors"></a>混合カーソル
混合カーソル、キーセット ドリブン カーソルと動的カーソルの組み合わせです。 結果セットが大きすぎるをある程度結果セット全体のキーを保存するときに使用されます。 混合カーソルを実装するは、結果セット全体よりも小さくなりますが、行セットよりも大きいキーセットを作成します。  
  
 動作は、アプリケーションは、キーセット内でスクロールする限り、キーセット ドリブンです。 キーセットの外部アプリケーションをスクロールするときの動作は動的: カーソルを要求された行をフェッチし、新しいキーセットを作成します。 新しいキーセットを作成した後、動作は、そのキーセット内でキーセット ドリブンに戻ります。  
  
 たとえば、結果セット 1,000 行があり、100 のキーセットのサイズと行セット サイズが 10 の混在のカーソルを使用します。 最初の行セットをフェッチすると、カーソルは、最初の 100 行のキーから成るキーセットを作成します。 要求どおりにも、最初の 10 個の行を返します。  
  
 もう 1 つのアプリケーションの削除行 11 および 101 を今すぐとします。 カーソルが行 11 を取得しようとすると、その発生する形の穴をこの行のキーを持つ行が存在しないためこれは、キーセット ドリブンの動作です。 カーソルが 101 行を取得しようとすると、カーソルが検出されません、行のキーがあるないため、行が不足していること。 代わりに、構成していた行 102 が取得されます。 これは、動的カーソルの動作です。  
  
 キーセットのサイズが結果セットのサイズに等しい場合に、混合カーソルはキーセット ドリブン カーソルと同じです。 キーセットのサイズが 1 に等しい場合に、混合カーソルは dynamic カーソルと同じです。
