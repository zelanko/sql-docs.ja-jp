---
title: '手順 4b: 行数を取得する |Microsoft Docs'
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302963"
---
# <a name="step-4b-fetch-the-row-count"></a>手順 4b: 行数をフェッチする
次の手順では、次の図に示すように行数を取得します。  
  
 ![行数のフェッチ](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 手順 3. で実行したステートメントが**UPDATE**、 **DELETE**、または**INSERT**ステートメントであった場合、アプリケーションは**SQLRowCount**を使用して影響を受ける行の数を取得します。 詳細については、「[影響を受ける行の数の決定](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)」を参照してください。  
  
 これで、アプリケーションは手順3に戻り、同じトランザクション内で別のステートメントを実行します。または、手順5に進み、トランザクションをコミットまたはロールバックします。
