---
title: SQLGetDiagField を呼び出して |Microsoft ドキュメント
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
- application upgrades [ODBC], SQLGetDiagField
- backward compatibility [ODBC], SqlGetDiagField
- upgrading applications [ODBC], SQLGetDiagField
- SQLGetDiagField function [ODBC], calling
- compatibility [ODBC], SQLGetDiagField
ms.assetid: 3c4fb606-b81c-4f11-9820-f0a54e3bc401
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5aeb241b97526af622fe8c9fc3bc8a044a2bf9d2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="calling-sqlgetdiagfield"></a>SQLGetDiagField を呼び出し
ODBC 3 時にします。*x*アプリケーション呼び出し**SQLGetDiagField** ODBC 2 で*.x*ドライバー、ドライバーは SQL_SUCCESS と内の適切な情報を返すは *\*DiagInfoPtr*場合、 *DiagIdentifier*引数は SQL_DIAG_CLASS_ORIGIN SQL_DIAG_CLASS_SUBCLASS_ORIGIN、SQL_DIAG_CONNECTION_NAME、SQL_DIAG_MESSAGE_TEXT、SQL_DIAG_NATIVE SQL_DIAG_SQL_DIAG_RETURNCODE、SQL_DIAG_SERVER_NAME、または SQL_DIAG_SQLSTATE 数。 その他のすべての診断フィールドには、SQL_ERROR が返されます。
