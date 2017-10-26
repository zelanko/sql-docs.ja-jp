---
title: "記述子を暗黙的に割り当てられた |Microsoft ドキュメント"
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
- descriptors [ODBC], allocating and freeing
- implicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 9f88c863-affc-4ab4-a558-63a3ef766f37
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0746c31b05302eba9cd1fcf4104336ca139b6938
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="implicitly-allocated-descriptors"></a>暗黙的に割り当てられた記述子
ステートメント ハンドルを割り当てるときに、アプリケーションは暗黙的に 4 つの記述子の 1 つのセットを割り当てます。 アプリケーションでは、ステートメント ハンドルの属性として記述子を暗黙的に割り当てられているこれらのハンドルを取得できます。 アプリケーションでは、ステートメント ハンドルを解放、ドライバーは、そのハンドルに暗黙的に割り当てられているすべての記述子を解放します。

