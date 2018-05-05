---
title: '手順 4 b: 行の数をフェッチ |Microsoft ドキュメント'
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
- fetches [ODBC], fetching row count
- row count [ODBC]
- application process [ODBC], fetching row count
ms.assetid: 3af481b1-d694-446e-948d-e3a5edcad050
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b90259758ceab600abce600bdfdab6edc52f506
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="step-4b-fetch-the-row-count"></a>手順 4 b: 行の数を取得
次の手順は、次の図に示すように、行の数をフェッチするは。  
  
 ![行の数のフェッチ](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 手順 3. で実行されたステートメントだった場合、**更新**、**削除**、または**挿入**ステートメントでは、アプリケーションが影響を受ける行の数を取得**SQLRowCount**です。 詳細については、次を参照してください。[の影響を受ける行の数を決定する](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)です。  
  
 今すぐ、アプリケーションを同じトランザクションで別のステートメントを実行する 3 ステップに戻るか、手順 5. をコミットまたはロールバック、トランザクションが続行されます。
