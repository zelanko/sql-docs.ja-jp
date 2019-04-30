---
title: SQLGetTypeInfo (dBASE ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLGetTypeInfo
ms.assetid: 6e9ce02b-97c7-4c1a-91e0-829df7459c84
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 90bfbe29fd011f8b62527854f0ca5a179d8f63cc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63224528"
---
# <a name="sqlgettypeinfo-dbase-driver"></a>SQLGetTypeInfo (dBASE ドライバー)
> [!NOTE]  
>  このトピックでは、dBASE ドライバー固有の情報を提供します。 この関数の詳細については、該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)します。  
  
 によって生成されたテーブルの型 (TYPE_NAME) の名前が返される**SQLGetTypeInfo**データ ソースで最もよく使用する名前になります。  
  
 SQL_ALL_EXCEPT_LIKE が返されます、検索可能な列で、バイトのカウンター、Double、1 つ、Long、Short データ型。 (LIKE 機能は、値を比較を実行し、ODBC 標準変換関数を使用する文字に変換することで実現できます)。
