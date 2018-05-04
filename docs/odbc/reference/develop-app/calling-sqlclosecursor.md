---
title: SQLCloseCursor を呼び出して |Microsoft ドキュメント
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
ms.topic: conceptual
helpviewer_keywords:
- application upgrades [ODBC], SQLCloseCursor
- backward compatibility [ODBC], SqlCloseCursor
- SQLCloseCursor function [ODBC], calling
- upgrading applications [ODBC], SQLCloseCursor
- compatibility [ODBC], SQLCloseCursor
ms.assetid: ef448c39-a9ad-4f07-8ef3-65bd4cef672a
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ad8a1d13091dd9413afb79b17eb701688d7f902
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="calling-sqlclosecursor"></a>SQLCloseCursor を呼び出す
**SQLCloseCursor**とほぼ同じ**SQLFreeStmt** SQL_CLOSE で、ドライバー マネージャーがマップされていないこの関数。 置換関数ができるように、既存のマップされた ODBC 2 *.x*アプリケーションは、ODBC 3 を簡単に移動できます*。x*新しい関数を使用しています。 このような移動すると、新しい ODBC 3 の使用を開始するには、このようなアプリケーションのやすくなります。*x*モジュール形式で、条件付きコード内で機能します。 **SQLCloseCursor**は新しい機能を表していません。 アプリケーションに移動してもメリットを利用できない**SQLCloseCursor**から**SQLFreeStmt** SQL_CLOSE とします。
