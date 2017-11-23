---
title: "SQLGetTypeInfo (Paradox ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLGetTypeInfo
ms.assetid: e65063c7-ba9e-4cf0-ac13-4bb5bd2937db
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dd0af7262ffa96d574913b56b18275b1bf2c27b7
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlgettypeinfo-paradox-driver"></a>SQLGetTypeInfo (Paradox ドライバー)
> [!NOTE]  
>  このトピックでは、Paradox ドライバー固有の情報を提供します。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 によって生成されるテーブルの型 (TYPE_NAME) の名前が返される**SQLGetTypeInfo**データ ソースによって最もよく使用される名前になります。  
  
 SQL_ALL_EXCEPT_LIKE が返されます、検索可能な列で、バイトのカウンター、Double、1 つの時間の長いと短い形式のデータ型。 (値を ODBC 標準の変換関数を使用する文字に変換することにより、LIKE の機能を実現できますと比較を実行します)。
