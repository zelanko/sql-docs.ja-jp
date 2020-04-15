---
title: 'ステップ 4b: 行数を取得する |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- fetches [ODBC], fetching row count
- row count [ODBC]
- application process [ODBC], fetching row count
ms.assetid: 3af481b1-d694-446e-948d-e3a5edcad050
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31ccbd15ae435165ea007fa9f3c0505c1dcc5aa0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302963"
---
# <a name="step-4b-fetch-the-row-count"></a>手順 4b: 行数をフェッチする
次の手順では、次の図に示すように、行数を取得します。  
  
 ![行数のフェッチ](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 手順 3 で実行したステートメントが**UPDATE** **、DELETE、** または**INSERT**ステートメントの場合、アプリケーションは**SQLRowCount**を使用して影響を受ける行の数を取得します。 詳細については、「[影響を受ける行の数の決定](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)」を参照してください。  
  
 アプリケーションは、同じトランザクションで別のステートメントを実行するためにステップ 3 に戻るか、トランザクションをコミットまたはロールバックするステップ 5 に進みます。
