---
title: キーセット駆動型カーソルの使用に関する制限 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2aeb5a0c50192118dfff8ed7d866c3911c2b4007
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284152"
---
# <a name="limitations-of-using-keyset-driven-cursors"></a>キーセット ドリブン カーソルの使用に関する制限
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、Oracle によって提供される ODBC ドライバーを使用します。  
  
 クエリを実行するテーブルの ROWID 列を 1 つだけ取得できる必要があります。 キーセット ドリブン カーソルは、DISTINCT 句、GROUP BY 句、UNION 句、インターセクト 句、または MINUS 句を含む結合、クエリ、またはステートメントには使用できません。  
  
 また、アプリケーションでテーブルの別名を使用している場合、キーセット ドリブン カーソルは機能しません。前方専用カーソルまたは静的カーソルの種類が必要です。 テーブルの別名でキーセットカーソルタイプを使用すると、次のエラーが発生します: "[Microsoft][Oracle 用 ODBC ドライバー]結合時にキーセットドリブン カーソルを使用できません。?ユニオン、交差、またはマイナスまたは読み取り専用の結果セットで。  
  
> [!NOTE]  
>  Oracle サーバーに送信される SQL ステートメントをドライバーが処理する方法のため、Oracle は内部的に次のエラー メッセージを返します: "ORA-00964: テーブル名は FROM リストにありません。
