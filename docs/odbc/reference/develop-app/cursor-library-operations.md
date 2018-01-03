---
title: "カーソル ライブラリの操作 |Microsoft ドキュメント"
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
- ODBC cursor library [ODBC], backward compatibility
- compatibility [ODBC], cursor library
- upgrading applications [ODBC], cursor library
- application upgrades [ODBC], cursor library
- backward compatibility [ODBC], cursor library
- cursor library [ODBC], backward compatibility
ms.assetid: 04d514b1-dc4d-4b84-bf35-60f4657ef1f6
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7e391cea65c366028d90ae61966e648e8d592145
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="cursor-library-operations"></a>カーソル ライブラリ操作
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 ODBC 2 を扱うアプリケーション*.x*ドライバーは ODBC 3 への呼び出しを実行します*。x*カーソル ライブラリ、アプリケーションは、ODBC 3 を使用可能である可能性があります*。x* ODBC 2 でサポートされていない機能*.x*ドライバー。 アプリケーション ライターは、これらの機能は、使用方法、ただし、注意が必要でする必要があります。 ODBC 3 を使用します。*x*カーソル ライブラリでは、ODBC 2 加えません*.x* ODBC 3 にドライバー *。x*ドライバー。
