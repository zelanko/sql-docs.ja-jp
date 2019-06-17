---
title: 手順 2:アプリケーションの初期化 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- initializing applications [ODBC]
- application process [ODBC], initializing applications
ms.assetid: 23a7a230-ae2c-4a5e-9760-d2e17f92c389
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0d25173dc8dc14aa1ed41a4a88496ef654e2ff0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63149184"
---
# <a name="step-2-initialize-the-application"></a>手順 2:アプリケーションを初期化する
2 番目の手順は、アプリケーションを初期化するためには次の図に示すようにします。 正確にどのようなここでは、アプリケーションによって異なります。  
  
 ![ODBC アプリケーションの初期化を示しています](../../../odbc/reference/develop-app/media/pr12.gif "pr12。")  
  
 この時点では使用する一般的な**SQLGetInfo**ドライバーの機能を検出します。 詳細については、次を参照してください。[使用するデータベース機能を検討して](../../../odbc/reference/develop-app/considering-database-features-to-use.md)します。  
  
 すべてのアプリケーションでのステートメント ハンドルを割り当てる必要があります**SQLAllocHandle**、多くのアプリケーションで、カーソルの種類などのステートメント属性を設定して**SQLSetStmtAttr**します。 詳細については、次を参照してください。[ステートメント ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md)と[ステートメント属性](../../../odbc/reference/develop-app/statement-attributes.md)します。
