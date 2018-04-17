---
title: 記述子を暗黙的に割り当てられた |Microsoft ドキュメント
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
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- implicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 9f88c863-affc-4ab4-a558-63a3ef766f37
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0553943e33ac71095cd040c9c375d055dc46c1f9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="implicitly-allocated-descriptors"></a>暗黙的に割り当てられた記述子
ステートメント ハンドルを割り当てるときに、アプリケーションは暗黙的に 4 つの記述子の 1 つのセットを割り当てます。 アプリケーションでは、ステートメント ハンドルの属性として記述子を暗黙的に割り当てられているこれらのハンドルを取得できます。 アプリケーションでは、ステートメント ハンドルを解放、ドライバーは、そのハンドルに暗黙的に割り当てられているすべての記述子を解放します。
