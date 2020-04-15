---
title: SQL 拡張フェッチ (カーソル ライブラリ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExtendedFetch function [ODBC], Cursor Library
ms.assetid: 06fbf06f-127b-475c-b636-7b784918475d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fe39b2d2cbbaf72ce3844c35187040589d1dac58
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302063"
---
# <a name="sqlextendedfetch-cursor-library"></a>SQLExtendedFetch (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソル ライブラリでの**SQLExtendedFetch**関数の使用について説明します。 **SQLExtendedFetch**の一般的な情報については、「 [SQLExtendedFetch 関数](../../../odbc/reference/syntax/sqlextendedfetch-function.md)」を参照してください。  
  
 カーソル ライブラリは、ドライバーで**SQLFetch**を繰り返し呼び出すことによって**SQLExtendedFetch**を実装します。  
  
 カーソル ライブラリでは、SQL_FETCH_BOOKMARKの*フェッチオリエンテーション*を使用した**SQLExtendedFetch**の呼び出しがサポートされています。  
  
 カーソル ライブラリを使用する場合 **、SQLExtendedFetch**の呼び出しを **、SQLFetchScroll**または**SQLFetch**の呼び出しと混在することはできません。
