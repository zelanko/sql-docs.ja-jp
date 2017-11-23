---
title: "手順 2: アプリケーションの初期化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- initializing applications [ODBC]
- application process [ODBC], initializing applications
ms.assetid: 23a7a230-ae2c-4a5e-9760-d2e17f92c389
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3aee15e4a528c7848a03ec4695a3ffd23edf106f
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="step-2-initialize-the-application"></a>手順 2: アプリケーションを初期化します。
2 番目の手順は、次の図に示すように、アプリケーションを初期化するためにです。 完全に新機能はここで、アプリケーションによって異なります。  
  
 ![ODBC アプリケーションの初期化を示しています](../../../odbc/reference/develop-app/media/pr12.gif "pr12。")  
  
 この時点では使用する一般的な**SQLGetInfo**ドライバーの機能を検出します。 詳細については、次を参照してください。[使用するデータベース機能を検討して](../../../odbc/reference/develop-app/considering-database-features-to-use.md)です。  
  
 すべてのアプリケーションを使用して、ステートメント ハンドルを割り当てる必要があります**SQLAllocHandle**、多くのアプリケーションで、カーソルの種類などのステートメント属性を設定して**SQLSetStmtAttr**です。 詳細については、次を参照してください。[ステートメント ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md)と[ステートメント属性](../../../odbc/reference/develop-app/statement-attributes.md)です。
