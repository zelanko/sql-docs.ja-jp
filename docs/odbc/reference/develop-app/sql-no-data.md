---
title: SQL_NO_DATA が |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- application upgrades [ODBC], SQL_NO_DATA
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
- upgrading applications [ODBC], SQL_NO_DATA
ms.assetid: 07a4144a-a548-4578-b2be-715c3cf73bf8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 749351694a41764b9b5cc8bf3421340d62626aaf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62445964"
---
# <a name="sqlnodata"></a>SQL_NO_DATA
ODBC 3 時にします。*x*アプリケーション呼び出し**SQLExecDirect**、 **SQLExecute**、または**SQLParamData** 、ODBC 2 *。x*検索の更新の実行、または、ドライバーは、データ ソースで行には影響しませんステートメントを削除するドライバーが SQL_SUCCESS、いない SQL_NO_DATA を返す必要があります。 ODBC 2 時にします。*x*または ODBC 3 *。x*アプリケーションは、ODBC 3 の操作します *。x*ドライバー呼び出し**SQLExecDirect**、 **SQLExecute**、または**SQLParamData**と同じ結果が、ODBC 3 *。x*ドライバーが SQL_NO_DATA を返す必要があります。
