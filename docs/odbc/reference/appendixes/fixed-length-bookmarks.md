---
title: 固定長ブックマーク |Microsoft ドキュメント
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
- backward compatibility [ODBC], bookmarks
- bookmarks [ODBC]
- compatibility [ODBC], bookmarks
- fixed-length bookmarks [ODBC]
ms.assetid: cbd8185e-fb03-408f-b80b-1a2e164534fd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 797a23c4fea5692cd01ce9fd05b56aeac27c3329
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="fixed-length-bookmarks"></a>固定長のブックマーク
場合、ODBC 3*.x*ドライバーは、ODBC 2 を使用する必要があります*。x*アプリケーション使用の固定長ブックマーク、ドライバーは、次をサポートする必要があります。  
  
-   SQL_USE_BOOKMARKS ステートメント オプションの値として SQL_UB_ON です。 (ODBC 3 SQL_UB_ON は推奨されなくなりました*.x*)。  
  
-   SQL_GET_BOOKMARK ステートメントのオプションです。
