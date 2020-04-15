---
title: SQLRowCount (カーソル ライブラリ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLRowCount function [ODBC], Cursor Library
ms.assetid: 781cf5a5-325e-4523-8633-d96d9e98277c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bf9fe597f54ecb4bc82439251e2228ac5fdc4ea3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300592"
---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソル ライブラリで**の SQLRowCount**関数の使用について説明します。 **SQLRowCount**の一般的な情報については、「 [SQLRowCount 関数](../../../odbc/reference/syntax/sqlrowcount-function.md)」を参照してください。  
  
 アプリケーションがカーソルに関連付けられたステートメントを使用して**SQLRowCount**を呼び出すと、カーソル ライブラリは、ドライバーから取得したデータの行数を返します。  
  
 アプリケーションが位置指定更新または削除ステートメントに関連付けられたステートメントを使用して**SQLRowCount**を呼び出すと、カーソル ライブラリはステートメントの影響を受ける行数を返します。  
  
 アプリケーションが**SELECT**ステートメントの後に**SQLRowCount**を呼び出すと、カーソル ライブラリは -1 を返します。
