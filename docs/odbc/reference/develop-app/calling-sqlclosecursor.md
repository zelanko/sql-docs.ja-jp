---
title: を呼び出す |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application upgrades [ODBC], SQLCloseCursor
- backward compatibility [ODBC], SqlCloseCursor
- SQLCloseCursor function [ODBC], calling
- upgrading applications [ODBC], SQLCloseCursor
- compatibility [ODBC], SQLCloseCursor
ms.assetid: ef448c39-a9ad-4f07-8ef3-65bd4cef672a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2feab58de28e39747a1d9c819f9f15426b156151
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306275"
---
# <a name="calling-sqlclosecursor"></a>SQLCloseCursor の呼び出し
**SQLCloseCursor**は、SQL_CLOSEを持つ**SQLFreeStmt**とほぼ同じであるため、ドライバー マネージャーはこの関数をマップしません。 置換関数は、既存の ODBC *2.x*アプリケーションが新しい関数を使用して ODBC *3.x*に簡単に移動できるようにマップされます。 このような移行により、このようなアプリケーションは、条件付きコード内での新しい ODBC *3.x*機能をモジュラー方式で使用し始めるのが容易になります。 **SQLCloseCursor は**、新しい機能を表していません。 アプリケーションは、SQL_CLOSEを使用して**SQLFreeStmt**から**SQLCloseCursor**に移動しても利点を得ません。
