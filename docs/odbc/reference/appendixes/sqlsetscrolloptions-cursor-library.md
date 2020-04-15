---
title: スクロールオプション (カーソル ライブラリ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Cursor Library
ms.assetid: c5c0ac6d-a6c1-4077-8186-1644df1944f8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0099ca5e9bcb3aefdd86e0132f52d110ab64e8a4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304913"
---
# <a name="sqlsetscrolloptions-cursor-library"></a>SQLSetScrollOptions (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソル ライブラリでの**SQLSetScrollOptions**関数の使用について説明します。 一般的な情報については、「 SQL**セットスクロール**[オプション関数](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)」を参照してください。  
  
 カーソル ライブラリは、後方互換性を維持するためにのみ**SQLSetScrollOptions**をサポートしています。アプリケーションでは、代わりにSQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_TYPE、およびSQL_ATTR_ROW_ARRAY_SIZEステートメント属性を使用する必要があります。
