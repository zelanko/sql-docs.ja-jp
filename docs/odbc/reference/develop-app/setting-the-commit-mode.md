---
title: コミット モードの設定 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], commit modes
- committing transactions [ODBC]
- commit modes [ODBC]
ms.assetid: b60d0d74-0655-4013-8d5a-bc1866eaa166
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: efc999a3644a9146e7195f0bbbb07d130172d30d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62445934"
---
# <a name="setting-the-commit-mode"></a>コミット モードの設定
アプリケーションでは、SQL_ATTR_AUTOCOMMIT 接続属性を持つ、トランザクション モードを指定します。 既定では ODBC トランザクション自動コミット モードでは (場合を除き、 **SQLSetConnectAttr**と**SQLSetConnectOption**はサポートされていませんはほとんどありません)。 自動コミット モードに手動コミット モードから自動的に切り替え、接続での任意の開いているトランザクションをコミットします。
