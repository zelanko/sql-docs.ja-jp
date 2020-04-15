---
title: コネクトオプション (エクセル ドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectOption function [ODBC], Excel Driver
- Excel driver [ODBC], SQLSetConnectOption
ms.assetid: 528d21d1-4516-4497-9da4-7b87d77e622a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7b9ddd764823b4ed89d9aae7055cf966f9f840a3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301513"
---
# <a name="sqlsetconnectoption-excel-driver"></a>SQLSetConnectOption (Excel ドライバー)
> [!NOTE]  
>  このトピックでは、Excel ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
|オプション|解説|  
|-------------|-------------|  
|SQL_ACCESS_MODE|fOption SQL_ACCESS_MODEは、SQL_MODE_READ_ONLYまたはSQL_MODE_READ_WRITEに設定できます。 ただし、SQL_ACCESS_MODEがSQL_MODE_READ_ONLYに設定されている場合、ドライバーは更新を防止しません。|  
|SQL_AUTOCOMMIT|Microsoft Excel ドライバは、トランザクションをサポートしていないため、SQL_AUTOCOMMITが ON (既定の状態) に設定されている場合にのみサポートされます。|  
|SQL_CURRENT_QUALIFIER|サポートされています。|  
|SQL_LOGIN_TIMEOUT|サポートされていません。|  
|SQL_OPT_TRACE|サポートされています。|  
|SQL_OPT_TRACEFILE|サポートされています。|  
|SQL_PACKET_SIZE|サポートされていません。|  
|SQL_QUIET_MODE|サポートされていません。|  
|SQL_TRANSLATE_DLL|サポートされていません。|  
|SQL_TRANSLATION_OPTION|サポートされていません。|  
|SQL_TXN_ISOLATION|サポートされていません。|
