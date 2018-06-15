---
title: 記述子を暗黙的に割り当てられた |Microsoft ドキュメント
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
- descriptors [ODBC], allocating and freeing
- implicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: 9f88c863-affc-4ab4-a558-63a3ef766f37
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8d805b110453c5fe0bb5be8c8df067c09ff8146e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32913877"
---
# <a name="implicitly-allocated-descriptors"></a>暗黙的に割り当てられた記述子
ステートメント ハンドルを割り当てるときに、アプリケーションは暗黙的に 4 つの記述子の 1 つのセットを割り当てます。 アプリケーションでは、ステートメント ハンドルの属性として記述子を暗黙的に割り当てられているこれらのハンドルを取得できます。 アプリケーションでは、ステートメント ハンドルを解放、ドライバーは、そのハンドルに暗黙的に割り当てられているすべての記述子を解放します。
