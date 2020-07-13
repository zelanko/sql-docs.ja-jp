---
title: SQLSetEnvAttr とカーソルライブラリ |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300522"
---
# <a name="sqlsetenvattr-and-the-cursor-library"></a>SQLSetEnvAttr およびカーソル ライブラリ
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新しい開発作業ではこの機能の使用を避け、現在この機能を使用しているアプリケーションの変更を検討してください。 Microsoft では、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソルライブラリでの**SQLSetEnvAttr**関数の使用について説明します。 **SQLSetEnvAttr**の一般的な情報については、「 [SQLSetEnvAttr 関数](../../../odbc/reference/syntax/sqlsetenvattr-function.md)」を参照してください。  
  
 カーソルライブラリは、アプリケーションのバージョンやドライバーのバージョンに関係なく、SQL_ATTR_ODBC_VERSION 環境属性の設定の影響を受けません。
