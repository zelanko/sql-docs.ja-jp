---
title: コミット モードの設定 |Microsoft ドキュメント
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
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
ms.assetid: b60d0d74-0655-4013-8d5a-bc1866eaa166
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 45e975f0cb9ccc78a7cadd4f1a71b046528a9c10
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="setting-the-commit-mode"></a>コミット モードの設定
アプリケーションは、SQL_ATTR_AUTOCOMMIT 接続属性を持つ、トランザクション モードを指定します。 ODBC トランザクションが自動コミット モードでは既定では、(場合を除き、 **SQLSetConnectAttr**と**SQLSetConnectOption**はサポートされていませんはほとんどありません)。 自動コミット モードに自動的に手動コミット モードから切り替え接続での任意の開いているトランザクションをコミットします。
