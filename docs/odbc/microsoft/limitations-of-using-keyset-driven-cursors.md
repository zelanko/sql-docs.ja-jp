---
title: キーセット ドリブン カーソルの使用の制限 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], cursors
- keyset-driven cursors [ODBC]
ms.assetid: 59d86fed-387c-4719-9550-36343e74da44
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c4910ebd2c6dd988e937f1e9d6a3281bb0e9741
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47668110"
---
# <a name="limitations-of-using-keyset-driven-cursors"></a>キーセット ドリブン カーソルの使用に関する制限
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 クエリ テーブルの 1 つの ROWID 列を取得できる必要があります。 結合、クエリ、または DISTINCT、GROUP BY、UNION、INTERSECT を含むステートメントまたは句マイナス、キーセット ドリブン カーソルは使用できません。  
  
 また、アプリケーションでは、テーブルの別名を使用する場合に、このキーセット ドリブン カーソルでは動作しません。順方向専用、または静的カーソルの種類が必要です。 キーセットを使用して、テーブルの別名とカーソルの種類で、次のエラーが発生します"[Microsoft] [Oracle 用 ODBC driver] は、キーセット ドリブン カーソルを使用できません参加で、和集合、交差するか、または読み取り専用にマイナスの結果セットです。"。  
  
> [!NOTE]  
>  ドライバーは、Oracle サーバーに送信される SQL ステートメントを処理する方法、により Oracle 内部的に返します、次のエラー メッセージ:"ORA 00964: テーブルの一覧から名前ではなく"。
