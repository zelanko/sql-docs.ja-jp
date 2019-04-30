---
title: '手順 4b: 行数のフェッチ |Microsoft Docs'
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
manager: craigg
ms.openlocfilehash: 3091d379bca6c061437e7767fdf6f99d69dc9861
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149154"
---
# <a name="step-4b-fetch-the-row-count"></a>手順 4b: 行数をフェッチする
次の手順は、次の図に示すように、行の数を取得するは。  
  
 ![行の数のフェッチ](../../../odbc/reference/develop-app/media/pr15.gif "pr15")  
  
 手順 3 で実行されるステートメントの場合、 **UPDATE**、**削除**、または**挿入**ステートメントでは、アプリケーションに影響を受けた行の数を取得します**SQLRowCount**します。 詳細については、次を参照してください。[の影響を受ける行の数を決定する](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)します。  
  
 アプリケーションは、同じトランザクション内で別のステートメントを実行する 3 ステップに戻るようになりましたかコミットするか、トランザクションをロールバックするために 5 のステップに進みます。
