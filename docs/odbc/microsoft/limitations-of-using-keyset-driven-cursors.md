---
title: "キーセット ドリブン カーソルの使用の制限事項 |Microsoft ドキュメント"
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
- ODBC driver for Oracle [ODBC], cursors
- keyset-driven cursors [ODBC]
ms.assetid: 59d86fed-387c-4719-9550-36343e74da44
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 54581e6bf4aceebc50a752ee460458671e8047bd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="limitations-of-using-keyset-driven-cursors"></a>キーセット ドリブン カーソルの使用に関する制限
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 クエリ テーブルの 1 つの ROWID 列を取得できる必要があります。 結合、クエリ、または DISTINCT、GROUP BY、UNION、INTERSECT を含むステートメントまたは句マイナス、キーセット ドリブン カーソルは使用できません。  
  
 また、アプリケーションでは、テーブルの別名を使用する場合は、キーセット ドリブン カーソルも動作しません。順方向専用、または静的カーソルの種類が必要です。 キーセットを使用して、カーソルの種類にテーブルの別名で、次のエラーが発生:"[Microsoft] [ODBC driver for Oracle] は、キーセット ドリブン カーソルを使用できません、結合に union、intersect または負符号、または読み取り専用の結果セットです"。  
  
> [!NOTE]  
>  ドライバーは、Oracle サーバーに送信する SQL ステートメントを処理するため、Oracle 内部的に返されます次のエラー メッセージ:"か 00964: テーブルの一覧からではなく名前です"。
