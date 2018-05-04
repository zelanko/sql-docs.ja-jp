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
ms.topic: conceptual
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
ms.openlocfilehash: bdf722c77071a3958f115e573bfe227f9561dd01
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="manual-commit-mode"></a>手動コミット モード
*手動コミット モードで*アプリケーションが呼び出すことによってトランザクションを明示的に完了する必要があります**SQLEndTran**をコミットまたはロールバックにします。 これは、ほとんどのリレーショナル データベースの通常のトランザクション モードです。  
  
 ODBC でのトランザクションを明示的に開始する必要はありません。 代わりに、トランザクションは、データベースで動作しているアプリケーションを起動するたびに、暗黙的に開始します。 データ ソースの明示的なトランザクションの開始に使用する場合は、アプリケーションがトランザクションを必要とするステートメントを実行し、現在のトランザクションが存在しないときに、ドライバーがそれを提供する必要があります。
