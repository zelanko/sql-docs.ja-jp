---
title: パラメータ値の配列 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arrays of parameter values [ODBC]
- parameter arrays [ODBC]
ms.assetid: 9b572c5b-1dfe-40af-bebd-051548ab6d90
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: eb9389c769e3a7bb0c39959a559531e8051a7bec
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298802"
---
# <a name="arrays-of-parameter-values"></a>パラメーター値の配列
アプリケーションがパラメータの配列を渡す場合に便利です。 たとえば、パラメーターの配列とパラメーター化された**INSERT**ステートメントを使用して、アプリケーションは一度に複数の行を挿入できます。 配列を使用する利点はいくつかあります。 まず、多くのステートメントのデータが 1 つのパケットで送信されるため (データ ソースがパラメータ配列をネイティブにサポートしている場合)、ネットワーク トラフィックが減少します。 次に、データ ソースによっては、同じ数の別々の SQL ステートメントを実行するよりも高速に配列を使用して SQL ステートメントを実行できます。 最後に、画面データの場合と同様に、データが配列に格納されている場合、アプリケーションは特定の列のすべての行を**SQLBindParameter**を 1 回呼び出してバインドし、1 つのステートメントを実行して更新できます。  
  
 残念ながら、多くのデータ ソースではパラメーター配列をサポートしていません。 ただし、ドライバーは、パラメーター値のセットごとに 1 回 SQL ステートメントを実行することで、パラメーター配列をエミュレートできます。 これにより、ドライバーは、各パラメーター セットに対して 1 回実行する予定のステートメントを準備できるため、速度が向上する可能性があります。 また、アプリケーション コードが単純になる可能性もあります。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [パラメーターのバインディング配列](../../../odbc/reference/develop-app/binding-arrays-of-parameters.md)  
  
-   [パラメーターの配列の使用](../../../odbc/reference/develop-app/using-arrays-of-parameters.md)
