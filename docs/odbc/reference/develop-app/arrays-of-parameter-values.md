---
title: パラメーター値の配列 |Microsoft ドキュメント
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
- arrays of parameter values [ODBC]
- parameter arrays [ODBC]
ms.assetid: 9b572c5b-1dfe-40af-bebd-051548ab6d90
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 38dc5fb0ed2286b3077e6198bc978808063b5d2f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="arrays-of-parameter-values"></a>パラメーター値の配列
アプリケーションのパラメーターの配列を渡すと便利です。 などのパラメーターとパラメーター化された配列を使用して**挿入**ステートメントでは、アプリケーションが、一度に多数の行を挿入できます。 これには配列を使用するいくつかの利点があります。 最初に、(データ ソースでは、パラメーター配列はネイティブ サポートしている) 場合、ステートメントの多くのデータが 1 つのパケットで送信されるため、ネットワーク トラフィックが減少します。 次に、一部のデータ ソースは、同じ数の個別の SQL ステートメントを実行するよりも高速に配列を使用する SQL ステートメントを実行できます。 最後に、する場合、配列内のデータが格納されているように、画面のデータの場合は、多くの場合、アプリケーション バインドできますのすべての行に 1 回の呼び出しを持つ特定の列の**SQLBindParameter**し、1 つのステートメントを実行することで更新します。  
  
 残念ながら、多くのデータ ソースは、パラメーター配列をサポートします。 ただし、ドライバーは、パラメーター値のセットごとに、SQL ステートメントを実行することによってパラメーター配列をエミュレートすることができます。 これには、ドライバーは、パラメーター セットごとに 1 回実行する予定があるステートメントを準備できますし、ため速度の増大につながることができます。 単純なアプリケーション コードになるも可能性があります。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [パラメーターのバインディング配列](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md)  
  
-   [パラメーターの配列の使用](../../../odbc/reference/develop-app/using-arrays-of-parameters.md)
