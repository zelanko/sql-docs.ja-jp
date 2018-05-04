---
title: 固定長ブックマーク |Microsoft ドキュメント
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
- backward compatibility [ODBC], bookmarks
- bookmarks [ODBC]
- compatibility [ODBC], bookmarks
- fixed-length bookmarks [ODBC]
ms.assetid: cbd8185e-fb03-408f-b80b-1a2e164534fd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b90454f8ecfa48081d17a71c63cc9f4ae670b4ff
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="fixed-length-bookmarks"></a>固定長のブックマーク
場合、ODBC 3 *.x*ドライバーは、ODBC 2 を使用する必要があります*。x*アプリケーション使用の固定長ブックマーク、ドライバーは、次をサポートする必要があります。  
  
-   SQL_USE_BOOKMARKS ステートメント オプションの値として SQL_UB_ON です。 (ODBC 3 SQL_UB_ON は推奨されなくなりました *.x*)。  
  
-   SQL_GET_BOOKMARK ステートメントのオプションです。
