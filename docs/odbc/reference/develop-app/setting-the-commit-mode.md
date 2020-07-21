---
title: コミットモードの設定 |Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f05aaca2349a612cda7c5b6b257e7a1d5a5ea9c5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299822"
---
# <a name="setting-the-commit-mode"></a>コミット モードの設定
アプリケーションでは、SQL_ATTR_AUTOCOMMIT 接続属性を使用してトランザクションモードを指定します。 既定では、ODBC トランザクションは自動コミットモードになっています ( **SQLSetConnectAttr**と**SQLSetConnectOption**がサポートされていない場合は、このようなことはほとんどありません)。 手動コミットモードから自動コミットモードに切り替えると、接続時に開いているトランザクションが自動的にコミットされます。
