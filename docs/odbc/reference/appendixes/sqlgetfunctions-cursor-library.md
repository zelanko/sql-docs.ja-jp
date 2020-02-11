---
title: SQLGetFunctions (カーソルライブラリ) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetFunctions function [ODBC], Cursor Library
ms.assetid: 931acd12-4eb6-4a78-9a77-157a18a9a2d0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1497a7d2ec5951feedb36831ab541413e57152f4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68073934"
---
# <a name="sqlgetfunctions-cursor-library"></a>SQLGetFunctions (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新しい開発作業ではこの機能の使用を避け、現在この機能を使用しているアプリケーションの変更を検討してください。 Microsoft では、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソルライブラリで**Sqlgetfunctions**関数を使用する方法について説明します。 **Sqlgetfunctions**に関する一般的な情報については、「 [Sqlgetfunctions 関数](../../../odbc/reference/syntax/sqlgetfunctions-function.md)」を参照してください。  
  
 **Sqlgetfunctions**を呼び出すと、カーソルライブラリは、ドライバーでサポートされている関数に加えて、 **SQLExtendedFetch**、 **sqlgetfunctions**、 **SQLSetPos**、および**SQLSetScrollOptions**をサポートしていることを返します。
