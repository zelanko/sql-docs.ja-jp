---
title: 手動コミットモード |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- rolling back transactions [ODBC]
- manual-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: 9c4b3931-e48b-4960-89a2-5697537e9f51
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2a00ff373e374d0940b3e7259eeb01e26b620cae
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81287876"
---
# <a name="manual-commit-mode"></a>手動コミット モード
*手動コミットモードでは、* アプリケーションは、 **SQLEndTran**を呼び出してコミットまたはロールバックすることにより、トランザクションを明示的に完了する必要があります。 これは、ほとんどのリレーショナルデータベースの通常のトランザクションモードです。  
  
 ODBC のトランザクションを明示的に開始する必要はありません。 代わりに、アプリケーションがデータベースで動作を開始するたびに、トランザクションが暗黙的に開始されます。 データソースに明示的なトランザクションの開始が必要な場合、アプリケーションがトランザクションを必要とするステートメントを実行し、現在のトランザクションが存在しないときは常に、ドライバーがそれを提供する必要があります。
