---
title: SQLNativeSql (カーソルライブラリ) |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0a8c42efbd87296cf7157d75d1848e4655247818
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125708"
---
# <a name="sqlnativesql-cursor-library"></a>SQLNativeSql (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新しい開発作業ではこの機能の使用を避け、現在この機能を使用しているアプリケーションの変更を検討してください。 Microsoft では、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソルライブラリでの**Sqlnativesql**関数の使用について説明します。 **Sqlnativesql**に関する一般的な情報については、「 [Sqlnativesql 関数](../../../odbc/reference/syntax/sqlnativesql-function.md)」を参照してください。  
  
 ドライバーがこの機能をサポートしている場合、カーソルライブラリはドライバーで**Sqlnativesql**を呼び出し、それに SQL ステートメントを渡します。 位置指定の更新、位置指定の削除、および**SELECT FOR update**ステートメントでは、カーソルライブラリによってステートメントが変更されてからドライバーに渡されます。  
  
> [!NOTE]  
>  カーソルライブラリは、 **Sqlnativesql**の*Instatementtext*引数で渡される位置指定の update または delete ステートメントでカーソル名が無効である場合、SQLSTATE 34000 (無効なカーソル名) を誤って返します。 **Sqlnativesql**は、ステートメントの準備または実行時にのみ返される構文エラーを返すことを意図していません。
