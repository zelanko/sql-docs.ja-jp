---
title: SQL フェッチ (カーソル ライブラリ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLFetch function [ODBC], Cursor Library
ms.assetid: 35a0d493-778b-4fb1-84ee-a13540e2fe0e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bee83ccb5497888b57a45673599af6b92931a704
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298722"
---
# <a name="sqlfetch-cursor-library"></a>SQLFetch (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソル ライブラリでの**SQLFetch**関数の使用について説明します。 **SQLFetch**の一般的な情報については、「 [SQL フェッチ関数](../../../odbc/reference/syntax/sqlfetch-function.md)」を参照してください。  
  
 カーソル ライブラリを使用する場合 **、SQLFetch**への呼び出しを**SQLFetchScroll**または**SQLExtendedFetch**の呼び出しと混在することはできません。  
  
 **SQLFetch**が 1 より大きい値に設定SQL_ATTR_ROW_ARRAY_SIZE呼び出された場合、カーソル ライブラリは、ドライバーに呼び出しを渡します。 ドライバが ODBC 2 の場合。*x*ドライバー、行セットのサイズは無視され **、SQLFetch**への呼び出しは、データの単一行を返します。  
  
 カーソル ライブラリが ODBC 2 で使用される場合。*x*ドライバーでは、(SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性で定義されている) バインド オフセットは **、SQLFetch**が呼び出されたときに使用されません。  
  
 カーソル ライブラリが読み込まれると、アプリケーションは**SQLFetch**を呼び出してブックマーク列をフェッチできません。 カーソル ライブラリは、ドライバーに**SQLFetch**への呼び出しを渡しますが、ブックマークを有効にし、ブックマーク列をバインドする関数の呼び出しは、カーソル ライブラリによってインターセプトされます。
