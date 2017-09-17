---
title: "手動コミット モード |Microsoft ドキュメント"
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
- rolling back transactions [ODBC]
- manual-commit mode [ODBC]
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
- transactions [ODBC], rolling back
ms.assetid: 9c4b3931-e48b-4960-89a2-5697537e9f51
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1a5f9d510d1a92ce8faf4fe29f3274afdba6f83b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="manual-commit-mode"></a>手動コミット モード
*手動コミット モードで*アプリケーションが呼び出すことによってトランザクションを明示的に完了する必要があります**SQLEndTran**をコミットまたはロールバックにします。 これは、ほとんどのリレーショナル データベースの通常のトランザクション モードです。  
  
 ODBC でのトランザクションを明示的に開始する必要はありません。 代わりに、トランザクションは、データベースで動作しているアプリケーションを起動するたびに、暗黙的に開始します。 データ ソースの明示的なトランザクションの開始に使用する場合は、アプリケーションがトランザクションを必要とするステートメントを実行し、現在のトランザクションが存在しないときに、ドライバーがそれを提供する必要があります。
