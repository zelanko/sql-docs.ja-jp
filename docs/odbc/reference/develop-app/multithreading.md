---
title: "マルチ スレッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC drivers [ODBC], thread-safe
- thread-safe drivers [ODBC]
- multithreaded applications [ODBC]
ms.assetid: cdfebdf5-12ff-4e28-8055-41f49b77f664
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9c49f5cf9e9a5082ff8fbdfcefc5b71656c61962
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="multithreading"></a>マルチ スレッド
マルチ スレッドのオペレーティング システムでドライバーにスレッド セーフであることがあります。 つまり、アプリケーションは複数のスレッドで同じハンドルを使用する場合があります。 これを実現する方法については、ドライバー固有およびドライバーに同時に 2 つの異なるスレッドで同じハンドルを使用しようとすると、シリアル化することが可能性があります。  
  
 通常、アプリケーションは、非同期処理ではなく複数のスレッドを使用します。 アプリケーションは、別のスレッドを作成、ODBC 関数を呼び出すには、および、メイン スレッドで処理を続行します。 はなく、非同期関数を常にポーリングする SQL_ATTR_ASYNC_ENABLE ステートメント属性を使用する場合は、アプリケーションは、[完了] 新しく作成されたスレッドを単にさせることができます。  
  
 呼び出してステートメント ハンドルをそのまま使用し、1 つのスレッドで実行している関数を取り消しできます**SQLCancel**同じステートメントでは、別のスレッドから処理します。 ドライバーを使用するシリアル化しないが**SQLCancel** 、この方法を保証はありませんその通話**SQLCancel**他方のスレッドで実行されている関数が実際に取り消されます。
