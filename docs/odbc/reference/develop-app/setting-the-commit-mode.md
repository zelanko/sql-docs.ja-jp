---
title: コミット モードの設定 |Microsoft ドキュメント
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
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
ms.assetid: b60d0d74-0655-4013-8d5a-bc1866eaa166
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c6d56a85716d88658c6e365484136460f7cce04b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32910537"
---
# <a name="setting-the-commit-mode"></a>コミット モードの設定
アプリケーションは、SQL_ATTR_AUTOCOMMIT 接続属性を持つ、トランザクション モードを指定します。 ODBC トランザクションが自動コミット モードでは既定では、(場合を除き、 **SQLSetConnectAttr**と**SQLSetConnectOption**はサポートされていませんはほとんどありません)。 自動コミット モードに自動的に手動コミット モードから切り替え接続での任意の開いているトランザクションをコミットします。
