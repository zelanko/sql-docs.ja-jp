---
title: SQL_NO_DATA |Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9a399a270eb1cd2f3daf9449c53b1f577a6b9545
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299792"
---
# <a name="sql_no_data"></a>SQL_NO_DATA
ODBC 3 の場合。*x*アプリケーションは、ODBC 2 で**SQLExecDirect**、 **Sqlexecute**、または**sqlparamdata**を呼び出します。*x*ドライバーデータソースの行に影響を与えない、検索された update ステートメントまたは delete ステートメントを実行するには、ドライバーが SQL_NO_DATA ではなく SQL_SUCCESS を返す必要があります。 ODBC 2 の場合。*x*または ODBC 3。*x*アプリケーションが ODBC 3 を使用して動作している。*x*ドライバーは、同じ結果 (ODBC 3) を使用して**SQLExecDirect**、 **Sqlexecute**、または**sqlparamdata**を呼び出します。*x*ドライバーは SQL_NO_DATA を返す必要があります。
