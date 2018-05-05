---
title: '手順 2: アプリケーションの初期化 |Microsoft ドキュメント'
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
- initializing applications [ODBC]
- application process [ODBC], initializing applications
ms.assetid: 23a7a230-ae2c-4a5e-9760-d2e17f92c389
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 85dff871a4b81551c699acc934aedb14c4f1725f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="step-2-initialize-the-application"></a>手順 2: アプリケーションを初期化します。
2 番目の手順は、次の図に示すように、アプリケーションを初期化するためにです。 完全に新機能はここで、アプリケーションによって異なります。  
  
 ![ODBC アプリケーションの初期化を示しています](../../../odbc/reference/develop-app/media/pr12.gif "pr12。")  
  
 この時点では使用する一般的な**SQLGetInfo**ドライバーの機能を検出します。 詳細については、次を参照してください。[使用するデータベース機能を検討して](../../../odbc/reference/develop-app/considering-database-features-to-use.md)です。  
  
 すべてのアプリケーションを使用して、ステートメント ハンドルを割り当てる必要があります**SQLAllocHandle**、多くのアプリケーションで、カーソルの種類などのステートメント属性を設定して**SQLSetStmtAttr**です。 詳細については、次を参照してください。[ステートメント ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md)と[ステートメント属性](../../../odbc/reference/develop-app/statement-attributes.md)です。
