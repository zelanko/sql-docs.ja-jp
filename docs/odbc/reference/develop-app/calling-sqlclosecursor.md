---
title: Sqlcloの呼び出し |Microsoft Docs
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
ms.openlocfilehash: 447a0892049317813fa9fe6986e6219922a11e28
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68068688"
---
# <a name="calling-sqlclosecursor"></a>SQLCloseCursor の呼び出し
**SqlcloSQLFreeStmt**は SQL_CLOSE とほぼ同じである**** ため、ドライバーマネージャーはこの機能をマップしません。 置換関数は、既存の ODBC 2.x*アプリケーションが*新しい関数を使用して簡単に odbc *3. x*に移動できるようにマップされます。 このような移動により、このようなアプリケーションでは、モジュール方式で条件付きコード内で新しい ODBC *3. x*機能を使い始めることが容易になります。 **Sqlcloセキュリティー**は、新しい機能を表していません。 アプリケーションでは、SQL_CLOSE を使用して**SQLFreeStmt**から**sqlcloに**移行しても利点は得られません。
