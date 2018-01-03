---
title: "ドライバーの種類 |Microsoft ドキュメント"
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
- driver compatibility issues [ODBC]
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
ms.assetid: 864c53c1-b68a-48b6-b6bc-5ecb520bb9dc
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c2068bb92d1aaa00debc46277c117d4134091666
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="types-of-drivers"></a>ドライバーの種類
ODBC ドライバーは、次のように分類できます。  
  
-   **32 ビット ODBC 2.**  
     ***x*ドライバー** 32 ビット バージョンのドライバーです。  
  
    -   ODBC 2 のみをエクスポート*.x*関数。  
  
    -   ODBC 2 が発生します。*x*動作の変更に対して動作します。  
  
-   **ISO と開いているグループに準拠したドライバー** 32 ビット バージョンのドライバーです。  
  
    -   グループを開くまたは ISO CLI のドキュメントに記載されているすべての関数をエクスポートします。 ODBC では非推奨機能の一部を含めます。  
  
    -   動作は、ODBC 3.0 動作の変更点です。  
  
    -   ODBC 3.0 のドライバー マネージャーを必ずしも通過しません。  
  
-   **ODBC 3.0 のドライバー** 32 ビット バージョンのドライバーです。  
  
    -   マイナス ODBC 3.0 では関数だけをエクスポートには、関数が使用されなくなりました。  
  
    -   ODBC 2 が発生することはできます。*x* SQL_ATTR_APP_ODBC_VERSION 環境属性に基づいて、動作または動作の変更に関して、ODBC 3.0 動作します。  
  
-   **ODBC 3.5 (またはそれ以降) ANSI ドライバー** 32 ビット バージョンのドライバーです。  
  
    -   マイナス ODBC 3.5 では関数だけをエクスポートには、関数が使用されなくなりました。  
  
    -   ODBC 2 が発生することはできます。*x* SQL_ATTR_APP_ODBC_VERSION 環境属性に基づいて、動作または ODBC 3.0 動作または動作の変更に関して、ODBC 3.5 動作します。  
  
-   **ODBC 3.5 (またはそれ以降) の Unicode ドライバー** 32 ビット バージョンのドライバーです。  
  
    -   ODBC 3.5 ANSI ドライバーのすべての機能をサポートしています。  
  
    -   すべての ODBC 文字列 Api の Unicode バージョンをエクスポートします。  
  
    -   データ ソース上の Unicode データの処理し、格納できます。  
  
> [!NOTE]  
>  16 ビット ODBC ドライバーは、ODBC 3 と直接は機能しません。*x*ドライバー マネージャー。 ただし、可能であれば、後で、3 つまでサンク 2.0 ODBC ドライバー マネージャーを使用する 16 ビット ドライバー用です。*x*ドライバー マネージャー。
