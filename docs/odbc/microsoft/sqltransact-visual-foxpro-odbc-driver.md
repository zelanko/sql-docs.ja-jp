---
title: SQLTransact (Visual FoxPro ODBC ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLTransact function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 92cf86c0-f7a8-44d7-b59f-a1342677440b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3910f24578bcbc409a84573e994c0680ed5949b2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299222"
---
# <a name="sqltransact-visual-foxpro-odbc-driver"></a>SQLTransact (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 サポート: 完全  
  
 ODBC API の準拠: コアレベル  
  
 接続に関連付けられているすべてのステートメントハンドル (*hstmt*s) のすべてのアクティブな操作、または環境ハンドル*henv*に関連付けられているすべての接続に対して、コミットまたはロールバックの操作を要求します。 **Sqltransact**は、[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)であるデータソースに対してのみ機能します。  
  
 手動モードでコミットが失敗した場合、トランザクションはアクティブのままです。トランザクションをロールバックするか、コミット操作を再試行するかを選択できます。 自動トランザクションモードでコミット操作が失敗した場合、トランザクションは自動的にロールバックされます。トランザクションを非アクティブにすることはできません。  
  
 詳細については、 *ODBC プログラマーリファレンス*の「 [sqltransact](../../odbc/reference/syntax/sqltransact-function.md) 」を参照してください。
