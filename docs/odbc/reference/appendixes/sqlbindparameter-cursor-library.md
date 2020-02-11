---
title: SQLBindParameter (カーソルライブラリ) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLBindParameter function [ODBC], Cursor Library
ms.assetid: 04c53e4c-cd1d-40b2-9997-684ebe43499f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7943987d52554e0f5cd7723e8c9ae8a0e3afddd2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093035"
---
# <a name="sqlbindparameter-cursor-library"></a>SQLBindParameter (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows では削除される予定です。 新しい開発作業ではこの機能の使用を避け、現在この機能を使用しているアプリケーションの変更を検討してください。 Microsoft では、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソルライブラリでの**SQLBindParameter**関数の使用について説明します。 **SQLBindParameter**の一般的な情報については、「 [SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)」を参照してください。  
  
 アプリケーションで**SQLBindParameter**を呼び出して、バインドされた列の C データ型、列サイズ、および10進数が同じである限り、パラメーターを再バインドすることができます。  
  
 カーソルライブラリでは、バインドオフセットを使用するための SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性の設定がサポートされています。 この再バインドを実行するには、**SQLBindParameter**を呼び出す必要はありません。  
  
 カーソルライブラリでは、実行時データパラメーターのバインドがサポートされています。
