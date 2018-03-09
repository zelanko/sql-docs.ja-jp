---
title: "固定長ブックマーク |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backward compatibility [ODBC], bookmarks
- bookmarks [ODBC]
- compatibility [ODBC], bookmarks
- fixed-length bookmarks [ODBC]
ms.assetid: cbd8185e-fb03-408f-b80b-1a2e164534fd
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d0b12009618489863c856d9b29433ff5146210ea
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="fixed-length-bookmarks"></a>固定長のブックマーク
場合、ODBC 3*.x*ドライバーは、ODBC 2 を使用する必要があります*。x*アプリケーション使用の固定長ブックマーク、ドライバーは、次をサポートする必要があります。  
  
-   SQL_USE_BOOKMARKS ステートメント オプションの値として SQL_UB_ON です。 (ODBC 3 SQL_UB_ON は推奨されなくなりました*.x*)。  
  
-   SQL_GET_BOOKMARK ステートメントのオプションです。
