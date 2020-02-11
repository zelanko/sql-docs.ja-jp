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
ms.openlocfilehash: 5877a6cb7a99803f854338321e333c87037c2e90
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67913582"
---
# <a name="fixed-length-bookmarks"></a>固定長のブックマーク
ODBC *3.x ドライバーが*固定長のブックマークを使用する odbc 2.x*アプリケーションで*動作する必要がある場合、ドライバーは次の機能をサポートする必要があります。  
  
-   SQL_USE_BOOKMARKS ステートメントオプションの値として SQL_UB_ON ます。 (SQL_UB_ON は ODBC 3.x では非推奨と*されます*)。  
  
-   SQL_GET_BOOKMARK ステートメントオプション。
