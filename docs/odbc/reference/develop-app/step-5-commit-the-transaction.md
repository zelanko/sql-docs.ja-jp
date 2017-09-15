---
title: "手順 5: トランザクションをコミットします |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application process [ODBC], committing transactions
- committing transactions [ODBC]
- transaction commit [ODBC]
ms.assetid: 311685e2-f7b5-4ddc-8020-59380cd2f035
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9ac53209063a1204b57e7183501b5901dc8ea248
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="step-5-commit-the-transaction"></a>手順 5: トランザクションをコミットします。
次の手順は、次の図に示すように、トランザクションをコミットするのには。  
  
 ![トランザクションをコミットする方法を示します](../../../odbc/reference/develop-app/media/pr16.gif "pr16")  
  
 5 番目の手順が呼び出されて**SQLEndTran**をコミットまたはトランザクションをロールバックします。 手動コミット; に、トランザクションのコミット モードを設定する場合にのみ、アプリケーションにこの手順を実行しますトランザクションのコミット モードが既定では、自動コミットの場合、トランザクションの値は、ステートメントが実行されたときに自動的にコミットされます。 詳細については、次を参照してください。[トランザクション](../../../odbc/reference/develop-app/transactions-odbc.md)です。  
  
 新しいトランザクションでステートメントを実行するには、アプリケーションは、手順 3 を返します。 切断するには、データ ソースからは、アプリケーションは、手順 6. に進みます。
