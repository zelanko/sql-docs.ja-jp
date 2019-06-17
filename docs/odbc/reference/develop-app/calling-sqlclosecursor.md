---
title: SQLCloseCursor の呼び出し |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7ee139dd652204c750c99d8bad8ab2b17c7c1ba1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63007808"
---
# <a name="calling-sqlclosecursor"></a>SQLCloseCursor の呼び出し
**SQLCloseCursor**とほぼ同じ**SQLFreeStmt** SQL_CLOSE で、ドライバー マネージャーがマップされていないこの関数。 置換関数は、既存するためのマップ ODBC 2 *.x*アプリケーションは、ODBC 3 を簡単に移動できます *。x*新しい関数を使用しています。 このような移動によって、新しい ODBC 3 の使用を開始するには、このようなアプリケーションを簡単にできます。*x*モジュール方式で条件付きコード内で機能します。 **SQLCloseCursor**の新しい機能を表していません。 アプリケーションが移行することによってメリットを利用できない**SQLCloseCursor**から**SQLFreeStmt** SQL_CLOSE とします。
