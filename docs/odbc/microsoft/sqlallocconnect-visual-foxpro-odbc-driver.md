---
title: SQLAllocConnect (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
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
- SQLAllocConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 70d48b12-def5-475c-b8e1-654a55fdfe0f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c7edefc6e5fcda420bb966f93aba8b15e20d1bd9
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlallocconnect-visual-foxpro-odbc-driver"></a>SQLAllocConnect (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 完全  
  
 ODBC API の準拠: コア レベル  
  
 接続ハンドルのメモリを割り当てます*hdbc*、によって識別される、環境内で*henv*です。 ドライバー マネージャーは、この呼び出しを処理し、ドライバーを呼び出します**SQLAllocConnect**されるたびに[SQLConnect](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md)、 **SQLBrowseConnect**、または[SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)と呼びます。  
  
 詳細については、次を参照してください。 [SQLAllocConnect](../../odbc/reference/syntax/sqlallocconnect-function.md)で、 *ODBC プログラマ リファレンス*です。
