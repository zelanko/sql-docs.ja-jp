---
title: 手動コミット モード |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
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
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3d0e5a4cc5bbda6c8ee4414854f390694297c94e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="manual-commit-mode"></a>手動コミット モード
*手動コミット モードで*アプリケーションが呼び出すことによってトランザクションを明示的に完了する必要があります**SQLEndTran**をコミットまたはロールバックにします。 これは、ほとんどのリレーショナル データベースの通常のトランザクション モードです。  
  
 ODBC でのトランザクションを明示的に開始する必要はありません。 代わりに、トランザクションは、データベースで動作しているアプリケーションを起動するたびに、暗黙的に開始します。 データ ソースの明示的なトランザクションの開始に使用する場合は、アプリケーションがトランザクションを必要とするステートメントを実行し、現在のトランザクションが存在しないときに、ドライバーがそれを提供する必要があります。
