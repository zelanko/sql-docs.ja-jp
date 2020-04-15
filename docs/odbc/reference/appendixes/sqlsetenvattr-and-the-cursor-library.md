---
title: SQL セットエンバトルとカーソル ライブラリ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetEnvAttr function [ODBC], Cursor Library
ms.assetid: 59cc8eae-09ae-4796-869a-c5806488ae83
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 42d6804bf8a3544de44c03266ce28712e1b04d90
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300522"
---
# <a name="sqlsetenvattr-and-the-cursor-library"></a>SQLSetEnvAttr およびカーソル ライブラリ
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソル ライブラリで**の SQLSetEnvAttr**関数の使用について説明します。 一般的な情報については、「 [SQL セットエンバトトル関数](../../../odbc/reference/syntax/sqlsetenvattr-function.md)」を参照してください。 **SQLSetEnvAttr**  
  
 カーソル ライブラリは、アプリケーションのバージョンやドライバーのバージョンに関係なく、SQL_ATTR_ODBC_VERSION環境属性の設定の影響を受けません。
