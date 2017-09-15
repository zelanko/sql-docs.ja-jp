---
title: "SQLAllocConnect (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLAllocConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 70d48b12-def5-475c-b8e1-654a55fdfe0f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5614b69fddd5b5430f15e8266bef6872d4294f4e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlallocconnect-visual-foxpro-odbc-driver"></a>SQLAllocConnect (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 完全  
  
 ODBC API の準拠: コア レベル  
  
 接続ハンドルのメモリを割り当てます*hdbc*、によって識別される、環境内で*henv*です。 ドライバー マネージャーは、この呼び出しを処理し、ドライバーを呼び出します**SQLAllocConnect**されるたびに[SQLConnect](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md)、 **SQLBrowseConnect**、または[SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)と呼びます。  
  
 詳細については、次を参照してください。 [SQLAllocConnect](../../odbc/reference/syntax/sqlallocconnect-function.md)で、 *ODBC プログラマ リファレンス*です。
