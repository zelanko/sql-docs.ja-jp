---
title: "コミット モードの設定 |Microsoft ドキュメント"
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
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
ms.assetid: b60d0d74-0655-4013-8d5a-bc1866eaa166
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6d0c38d70b859b1fb986ebaa366a5396159a95da
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="setting-the-commit-mode"></a>コミット モードの設定
アプリケーションは、SQL_ATTR_AUTOCOMMIT 接続属性を持つ、トランザクション モードを指定します。 ODBC トランザクションが自動コミット モードでは既定では、(場合を除き、 **SQLSetConnectAttr**と**SQLSetConnectOption**はサポートされていませんはほとんどありません)。 自動コミット モードに自動的に手動コミット モードから切り替え接続での任意の開いているトランザクションをコミットします。
