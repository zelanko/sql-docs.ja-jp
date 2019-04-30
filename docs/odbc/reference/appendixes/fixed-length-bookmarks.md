---
title: 固定長のブックマーク |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], bookmarks
- bookmarks [ODBC]
- compatibility [ODBC], bookmarks
- fixed-length bookmarks [ODBC]
ms.assetid: cbd8185e-fb03-408f-b80b-1a2e164534fd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e40947dc4dbad0830444870ea7e2d0c663490b25
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63188970"
---
# <a name="fixed-length-bookmarks"></a>固定長のブックマーク
場合、ODBC 3 *.x*ドライバーは ODBC 2 を使用する必要があります *。x*アプリケーションは固定長のブックマーク、ドライバーが、次をサポートする必要があります。  
  
-   SQL_UB_ON SQL_USE_BOOKMARKS ステートメント オプションの値として。 (SQL_UB_ON が ODBC 3 で非推奨と *.x*)。  
  
-   SQL_GET_BOOKMARK ステートメント オプション。
