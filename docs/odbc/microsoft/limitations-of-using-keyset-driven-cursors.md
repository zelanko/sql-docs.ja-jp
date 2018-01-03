---
title: "キーセット ドリブン カーソルの使用の制限事項 |Microsoft ドキュメント"
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
- ODBC driver for Oracle [ODBC], cursors
- keyset-driven cursors [ODBC]
ms.assetid: 59d86fed-387c-4719-9550-36343e74da44
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a6ecdac0639264140feb29cbe5023f81b407d231
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="limitations-of-using-keyset-driven-cursors"></a>キーセット ドリブン カーソルの使用に関する制限
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 クエリ テーブルの 1 つの ROWID 列を取得できる必要があります。 結合、クエリ、または DISTINCT、GROUP BY、UNION、INTERSECT を含むステートメントまたは句マイナス、キーセット ドリブン カーソルは使用できません。  
  
 また、アプリケーションでは、テーブルの別名を使用する場合は、キーセット ドリブン カーソルも動作しません。順方向専用、または静的カーソルの種類が必要です。 キーセットを使用して、カーソルの種類にテーブルの別名で、次のエラーが発生:"[Microsoft] [ODBC driver for Oracle] は、キーセット ドリブン カーソルを使用できません、結合に union、intersect または負符号、または読み取り専用の結果セットです"。  
  
> [!NOTE]  
>  ドライバーは、Oracle サーバーに送信する SQL ステートメントを処理するため、Oracle 内部的に返されます次のエラー メッセージ:"か 00964: テーブルの一覧からではなく名前です"。
