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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a43a78ad9453f65d9b12595851bd622f720b409a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68094223"
---
# <a name="setting-the-commit-mode"></a>コミット モードの設定
アプリケーションでは、SQL_ATTR_AUTOCOMMIT 接続属性を使用してトランザクションモードを指定します。 既定では、ODBC トランザクションは自動コミットモードになっています ( **SQLSetConnectAttr**と**SQLSetConnectOption**がサポートされていない場合は、このようなことはほとんどありません)。 手動コミットモードから自動コミットモードに切り替えると、接続時に開いているトランザクションが自動的にコミットされます。
