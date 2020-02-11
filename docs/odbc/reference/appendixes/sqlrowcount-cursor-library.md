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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: be902866cfcf98a10af2c3741926de8b7541bb79
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125597"
---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新しい開発作業ではこの機能の使用を避け、現在この機能を使用しているアプリケーションの変更を検討してください。 Microsoft では、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソルライブラリでの**SQLRowCount**関数の使用について説明します。 **SQLRowCount**の一般的な情報については、「 [SQLRowCount 関数](../../../odbc/reference/syntax/sqlrowcount-function.md)」を参照してください。  
  
 アプリケーションが、カーソルに関連付けられているステートメントを使用して**SQLRowCount**を呼び出すと、カーソルライブラリは、ドライバーから取得したデータの行の数を返します。  
  
 アプリケーションが、位置指定の update または delete ステートメントに関連付けられたステートメントを使用して**SQLRowCount**を呼び出すと、カーソルライブラリは、ステートメントの影響を受けた行数を返します。  
  
 アプリケーションが**SELECT**ステートメントの後に**SQLRowCount**を呼び出すと、カーソルライブラリは-1 を返します。
