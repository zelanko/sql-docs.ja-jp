---
title: SQLフリーストム (カーソルライブラリ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFreeStmt function [ODBC], Cursor Library
ms.assetid: 47bfbd4d-9453-4609-958d-1e05794cb223
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d78075593926c15dbaeb1904603b08e990f64983
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302023"
---
# <a name="sqlfreestmt-cursor-library"></a>SQLFreeStmt (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソル ライブラリでの**SQLFreeStmt**関数の使用について説明します。 一般的な情報については、 **SQLFreeStmt**[関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)を参照してください。  
  
 アプリケーションが **、SQLExtendedFetch 、SQLFetch** 、または**SQLFetchScroll**を呼び出した**SQLFetchScroll**後に、SQL_UNBIND オプションを指定して**SQLFreeStmt**を呼び出した場合、カーソル ライブラリはエラーを返します。 結果セット列をバインド解除する前に、アプリケーションは SQL_CLOSE オプションを指定して**SQLCloseCursor**または**SQLFreeStmt**を呼び出す必要があります。
