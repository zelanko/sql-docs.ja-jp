---
title: SQL セットコネクトアトル (カーソル ライブラリ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectAttr function [ODBC], Cursor Library
ms.assetid: 6f70bbd0-a057-49ef-8b05-4c80b58fc6e6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a87c85d727fb9eb2fc27613b9eecd3fe0ec51b58
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300542"
---
# <a name="sqlsetconnectattr-cursor-library"></a>SQLSetConnectAttr (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックでは、カーソル ライブラリでの**SQLSetConnectAttr**関数の使用について説明します。 一般的な情報については、 [SQL セットコネクトアットトル関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)を参照してください。 **SQLSetConnectAttr**  
  
 アプリケーションは、SQL_ATTR_ODBC_CURSORS属性を指定して**SQLSetConnectAttr**を呼び出して、カーソル ライブラリを常に使用するか、ドライバーがスクロール可能なカーソルをサポートしていない場合、または使用しない場合に使用するかどうかを指定します。 カーソル ライブラリは、ドライバーが**SQLGetInfo**でSQL_STATIC_CURSOR_ATTRIBUTES1情報の種類のSQL_CA1_RELATIVEを返す場合、スクロール可能なカーソルをサポートすることを前提としています。  
  
 アプリケーションは、接続を割り当てるハンドル*型のSQL_HANDLE_DBC*を使用して SQLAllocHandle を呼び出した後、およびデータ ソースに接続する前に **、SQLSetConnectAttr**を呼び出してカーソル ライブラリの使用法を指定する必要があります。 **SQLSetConnectAttr** 接続がアクティブな状態でアプリケーションが SQL_ATTR_ODBC_CURSORS属性を指定して**SQLSetConnectAttr**を呼び出した場合、カーソル ライブラリはエラーを返します。  
  
 接続に関連付けられたすべてのステートメントについてカーソル ライブラリでサポートされるステートメント属性を設定するには、アプリケーションは、データ ソースに接続した後、カーソルを開く前に、そのステートメント属性に対して**SQLSetConnectAttr**を呼び出す必要があります。 アプリケーションがステートメント属性を指定して**SQLSetConnectAttr**を呼び出し、その接続に関連付けられたステートメントでカーソルがオープンしている場合、カーソルがクローズされて再オープンされるまで、ステートメント属性はそのステートメントに適用されません。
