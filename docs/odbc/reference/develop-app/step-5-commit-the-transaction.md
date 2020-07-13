---
title: '手順 5: トランザクションをコミットする |Microsoft Docs'
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e348ce697e512f30db46d14535cf19bd6d530f61
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81283352"
---
# <a name="step-5-commit-the-transaction"></a>手順 5:トランザクションをコミットする
次の手順では、次の図に示すように、トランザクションをコミットします。  
  
 ![トランザクションのコミット方法の表示](../../../odbc/reference/develop-app/media/pr16.gif "pr16")  
  
 5番目の手順では、 **SQLEndTran**を呼び出してトランザクションをコミットまたはロールバックします。 アプリケーションは、トランザクションコミットモードを手動コミットに設定した場合にのみ、このステップを実行します。トランザクションコミットモードが自動コミット (既定) の場合、ステートメントの実行時にトランザクションは自動的にコミットされます。 詳細については、「[トランザクション](../../../odbc/reference/develop-app/transactions-odbc.md)」を参照してください。  
  
 新しいトランザクションでステートメントを実行するには、アプリケーションが手順 3. に戻ります。 データソースから切断するには、アプリケーションが手順 6. に進みます。
