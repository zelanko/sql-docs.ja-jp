---
title: SQLRowCount (カーソルライブラリ) |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300592"
---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新しい開発作業ではこの機能の使用を避け、現在この機能を使用しているアプリケーションの変更を検討してください。 Microsoft では、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソルライブラリでの**SQLRowCount**関数の使用について説明します。 **SQLRowCount**の一般的な情報については、「 [SQLRowCount 関数](../../../odbc/reference/syntax/sqlrowcount-function.md)」を参照してください。  
  
 アプリケーションが、カーソルに関連付けられているステートメントを使用して**SQLRowCount**を呼び出すと、カーソルライブラリは、ドライバーから取得したデータの行の数を返します。  
  
 アプリケーションが、位置指定の update または delete ステートメントに関連付けられたステートメントを使用して**SQLRowCount**を呼び出すと、カーソルライブラリは、ステートメントの影響を受けた行数を返します。  
  
 アプリケーションが**SELECT**ステートメントの後に**SQLRowCount**を呼び出すと、カーソルライブラリは-1 を返します。
