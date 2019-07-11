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
ms.openlocfilehash: 21af6ef1be21e000d25582151650f274fe3561a4
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793370"
---
# <a name="fixed-length-bookmarks"></a>固定長のブックマーク
場合、ODBC *3.x*ドライバーは ODBC を使用する必要があります*2.x*アプリケーションは固定長のブックマーク、ドライバーが、次をサポートする必要があります。  
  
-   SQL_UB_ON SQL_USE_BOOKMARKS ステートメント オプションの値として。 (SQL_UB_ON が ODBC で非推奨と*3.x*)。  
  
-   SQL_GET_BOOKMARK ステートメント オプション。
