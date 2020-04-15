---
title: マルチスレッド |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], thread-safe
- thread-safe drivers [ODBC]
- multithreaded applications [ODBC]
ms.assetid: cdfebdf5-12ff-4e28-8055-41f49b77f664
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c10d1b401ac780d24184c4c2337199e99973e916
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302419"
---
# <a name="multithreading"></a>マルチスレッド
マルチスレッド オペレーティング システムでは、ドライバーはスレッド セーフである必要があります。 つまり、アプリケーションが複数のスレッドで同じハンドルを使用できる必要があります。 この方法はドライバ固有であり、ドライバは 2 つの異なるスレッドで同じハンドルを同時に使用しようとする試みをシリアル化する可能性があります。  
  
 アプリケーションは、通常、非同期処理の代わりに複数のスレッドを使用します。 アプリケーションは、別のスレッドを作成し、そのスレッドに対して ODBC 関数を呼び出し、メイン スレッドで処理を続行します。 SQL_ATTR_ASYNC_ENABLE ステートメント属性を使用する場合のように、非同期関数を継続的にポーリングする必要が生じるのではなく、アプリケーションは新しく作成されたスレッドを終了させることができます。  
  
 ステートメント・ハンドルを受け入れ、あるスレッドで実行されている関数は、別のスレッドから同じステートメント・ハンドルを使用して**SQLCancel**を呼び出すことによって、取り消すことができます。 ドライバーは、この方法で**SQLCancel**の使用をシリアル化する必要はありませんが **、SQLCancel**を呼び出すと、他のスレッドで実行されている関数が実際にキャンセルされる保証はありません。
