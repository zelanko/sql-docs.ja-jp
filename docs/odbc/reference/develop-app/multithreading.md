---
title: マルチ スレッド |Microsoft ドキュメント
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
- ODBC drivers [ODBC], thread-safe
- thread-safe drivers [ODBC]
- multithreaded applications [ODBC]
ms.assetid: cdfebdf5-12ff-4e28-8055-41f49b77f664
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7cf1543a039c0928068209d1d79064b074fdc2f8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32912295"
---
# <a name="multithreading"></a>マルチ スレッド
マルチ スレッドのオペレーティング システムでドライバーにスレッド セーフであることがあります。 つまり、アプリケーションは複数のスレッドで同じハンドルを使用する場合があります。 これを実現する方法については、ドライバー固有およびドライバーに同時に 2 つの異なるスレッドで同じハンドルを使用しようとすると、シリアル化することが可能性があります。  
  
 通常、アプリケーションは、非同期処理ではなく複数のスレッドを使用します。 アプリケーションは、別のスレッドを作成、ODBC 関数を呼び出すには、および、メイン スレッドで処理を続行します。 はなく、非同期関数を常にポーリングする SQL_ATTR_ASYNC_ENABLE ステートメント属性を使用する場合は、アプリケーションは、[完了] 新しく作成されたスレッドを単にさせることができます。  
  
 呼び出してステートメント ハンドルをそのまま使用し、1 つのスレッドで実行している関数を取り消しできます**SQLCancel**同じステートメントでは、別のスレッドから処理します。 ドライバーを使用するシリアル化しないが**SQLCancel** 、この方法を保証はありませんその通話**SQLCancel**他方のスレッドで実行されている関数が実際に取り消されます。
