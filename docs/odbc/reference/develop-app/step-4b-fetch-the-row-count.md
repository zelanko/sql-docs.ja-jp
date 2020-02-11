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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9455c6589ed93a51e404f3e50d1cb86a0c0c8476
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114157"
---
# <a name="step-4b-fetch-the-row-count"></a>ステップ 4b: 行数のフェッチ
次の手順では、次の図に示すように行数を取得します。  
  
 ![行数のフェッチ](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 手順 3. で実行したステートメントが**UPDATE**、 **DELETE**、または**INSERT**ステートメントであった場合、アプリケーションは**SQLRowCount**を使用して影響を受ける行の数を取得します。 詳細については、「[影響を受ける行の数の決定](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)」を参照してください。  
  
 これで、アプリケーションは手順3に戻り、同じトランザクション内で別のステートメントを実行します。または、手順5に進み、トランザクションをコミットまたはロールバックします。
