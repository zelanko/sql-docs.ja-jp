---
title: "SQLSetConnectOption (テキスト ファイル ドライバー) |Microsoft ドキュメント"
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
- SQLSetConnectOption function [ODBC], Text File Driver
- text file driver [ODBC], SQLSetConnectOption
ms.assetid: b631a20c-2f60-4102-a61d-93b8780a4620
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8c03e4c6d53d9ae5055135b8dd4fe76509a448e3
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlsetconnectoption-text-file-driver"></a>SQLSetConnectOption (テキスト ファイル ドライバー)
> [!NOTE]  
>  このトピックでは、テキスト ファイル ドライバー固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
|fOption|解説|  
|-------------|-------------|  
|SQL_ACCESS_MODE|SQL_ACCESS_MODE fOption は、SQL_MODE_READ_ONLY または SQL_MODE_READ_WRITE のいずれかに設定することができます。 ただし、SQL_ACCESS_MODE が SQL_MODE_READ_ONLY に設定されている場合、ドライバーは更新を禁止できません。|  
|SQL_AUTOCOMMIT|テキスト ドライバーでは、トランザクションをサポートしていないために (既定の状態) に設定されている SQL_AUTOCOMMIT のみサポートされます。|  
|SQL_CURRENT_QUALIFIER|サポートされています。|  
|SQL_LOGIN_TIMEOUT|サポートされていません。|  
|SQL_OPT_TRACE|サポートされています。|  
|SQL_OPT_TRACEFILE|サポートされています。|  
|SQL_PACKET_SIZE|サポートされていません。|  
|SQL_QUIET_MODE|サポートされていません。|  
|SQL_TRANSLATE_DLL|サポートされていません。|  
|SQL_TRANSLATION_OPTION|サポートされていません。|  
|SQL_TXN_ISOLATION|サポートされていません。|
