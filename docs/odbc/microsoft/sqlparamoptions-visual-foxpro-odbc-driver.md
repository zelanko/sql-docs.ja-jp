---
title: SQLParamOptions (Visual FoxPro ODBC ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLParamOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 7f94a6e2-9c34-405c-b2b0-304d94269715
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a66f0cd3a17baa9a09a5eeef2ade3d730f0a206b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62636662"
---
# <a name="sqlparamoptions-visual-foxpro-odbc-driver"></a>SQLParamOptions (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックでには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の詳細については、該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)します。  
  
 サポート:[完全]  
  
 ODBC API 準拠:[レベル 1]  
  
 アプリケーションによって割り当てられたパラメーターのセットの複数の値を指定できるように[SQLBindParameter](../../odbc/microsoft/sqlbindparameter-visual-foxpro-odbc-driver.md)します。 パラメーターのセットに複数の値を指定する機能は、一括挿入し、さまざまなパラメーター値で複数回、同じ SQL ステートメントを処理するデータ ソースを必要とするその他の作業に適しています。 たとえば、アプリケーションが 3 つのパラメーターに関連付けられている一連の値を指定できます、**挿入**ステートメントし、実行、**挿入**3 つを実行するステートメントを 1 回の挿入操作です。  
  
 詳細については、次を参照してください。 [SQLParamOptions](../../odbc/reference/syntax/sqlparamoptions-function.md)で、 *ODBC プログラマ リファレンス*します。
