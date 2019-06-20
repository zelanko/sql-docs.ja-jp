---
title: 手順 5:トランザクションをコミット |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application process [ODBC], committing transactions
- committing transactions [ODBC]
- transaction commit [ODBC]
ms.assetid: 311685e2-f7b5-4ddc-8020-59380cd2f035
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 341f34afa1dbe65f4b83a46f461bb93f4fb4f4c8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63148945"
---
# <a name="step-5-commit-the-transaction"></a>手順 5:トランザクションをコミットする
次の手順は、次の図に示すように、トランザクションをコミットするは。  
  
 ![トランザクションをコミットする方法を示します](../../../odbc/reference/develop-app/media/pr16.gif "pr16")  
  
 5 番目の手順では呼び出しを**SQLEndTran**をコミットまたはトランザクションをロールバックします。 アプリケーションがトランザクションのコミット モードを設定; 手動コミットする場合は、この手順を実行します。トランザクションのコミット モードが既定では、この自動コミットの場合、トランザクションの値が、ステートメントが実行されたときに自動的にコミットします。 詳細については、次を参照してください。[トランザクション](../../../odbc/reference/develop-app/transactions-odbc.md)です。  
  
 新しいトランザクションでステートメントを実行するには、アプリケーションは、手順 3 を返します。 をデータ ソースから切断するには、は、アプリケーションは、手順 6. に進みます。
