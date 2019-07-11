---
title: SQLGetDiagField の呼び出し |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- application upgrades [ODBC], SQLGetDiagField
- backward compatibility [ODBC], SqlGetDiagField
- upgrading applications [ODBC], SQLGetDiagField
- SQLGetDiagField function [ODBC], calling
- compatibility [ODBC], SQLGetDiagField
ms.assetid: 3c4fb606-b81c-4f11-9820-f0a54e3bc401
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 42d24de7e5e94a3301653eb3082140e260a1e745
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793904"
---
# <a name="calling-sqlgetdiagfield"></a>SQLGetDiagField の呼び出し
ときに、ODBC *3.x*アプリケーション呼び出し**SQLGetDiagField** odbc *2.x*ドライバー、ドライバーは SQL_SUCCESS とで該当する情報を返すは *\*DiagInfoPtr*場合、 *DiagIdentifier*引数は、SQL_DIAG_CLASS_ORIGIN、SQL_DIAG_CLASS_SUBCLASS_ORIGIN、SQL_DIAG_CONNECTION_NAME、SQL_DIAG_MESSAGE_TEXT SQL_DIAG_ネイティブ、SQL_DIAG_NUMBER、SQL_DIAG_RETURNCODE、SQL_DIAG_SERVER_NAME、または SQL_DIAG_SQLSTATE します。 その他のすべての診断フィールドには、SQL_ERROR が返されます。
