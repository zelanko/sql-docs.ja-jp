---
title: をクリックします。マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLNativeSql function [ODBC], Cursor Library
ms.assetid: c4459092-1177-4b2a-b7f5-e0083d3bf2b2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 41f7617530f34d49852ca67db9f47cab94292385
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300572"
---
# <a name="sqlnativesql-cursor-library"></a>SQLNativeSql (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソル ライブラリで**の SQLNativeSql**関数の使用について説明します。 **一**般的な情報については、SQL[ネイティブSql 関数](../../../odbc/reference/syntax/sqlnativesql-function.md)を参照してください。  
  
 ドライバーがこの関数をサポートしている場合、カーソル ライブラリは、ドライバーで**SQLNativeSql**を呼び出し、SQL ステートメントを渡します。 位置指定更新、位置指定削除、**および SELECT FOR UPDATE**ステートメントの場合、カーソル ライブラリは、ドライバーに渡す前にステートメントを変更します。  
  
> [!NOTE]  
>  カーソル ライブラリは **、SQLNativeSql**の*InStatementText*引数で渡された位置指定更新または削除ステートメントでカーソル名が無効な場合、SQLSTATE 34000 (無効なカーソル名) を誤って返します。 **SQLNativeSql**は構文エラーを返すことを意図していません。
