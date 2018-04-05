---
title: SQLParamOptions (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント
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
- SQLParamOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 7f94a6e2-9c34-405c-b2b0-304d94269715
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ade98eb2f7d0096c1ef6bf28a7c5ab694f1b4853
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlparamoptions-visual-foxpro-odbc-driver"></a>SQLParamOptions (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 完全  
  
 レベル 1 の ODBC API への準拠:  
  
 により、アプリケーションによって割り当てられたパラメーターのセットに複数の値を指定する[SQLBindParameter](../../odbc/microsoft/sqlbindparameter-visual-foxpro-odbc-driver.md)です。 パラメーターのセットに複数の値を指定することは、一括挿入やさまざまなパラメーター値を複数回、同じ SQL ステートメントを処理するデータ ソースを必要とするその他の作業に役立ちます。 たとえば、アプリケーションが 3 つのパラメーターに関連付けられている一連の値を指定できます、**挿入**ステートメントし、実行、**挿入**3 つを実行するステートメントを 1 回の挿入操作です。  
  
 詳細については、次を参照してください。 [SQLParamOptions](../../odbc/reference/syntax/sqlparamoptions-function.md)で、 *ODBC プログラマ リファレンス*です。
