---
title: SQLAllocConnect (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント
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
- SQLAllocConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 70d48b12-def5-475c-b8e1-654a55fdfe0f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aebb1f4efbe916a550e4844fbb2890853839a997
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlallocconnect-visual-foxpro-odbc-driver"></a>SQLAllocConnect (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 完全  
  
 ODBC API の準拠: コア レベル  
  
 接続ハンドルのメモリを割り当てます*hdbc*、によって識別される、環境内で*henv*です。 ドライバー マネージャーは、この呼び出しを処理し、ドライバーを呼び出します**SQLAllocConnect**されるたびに[SQLConnect](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md)、 **SQLBrowseConnect**、または[SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)と呼びます。  
  
 詳細については、次を参照してください。 [SQLAllocConnect](../../odbc/reference/syntax/sqlallocconnect-function.md)で、 *ODBC プログラマ リファレンス*です。
