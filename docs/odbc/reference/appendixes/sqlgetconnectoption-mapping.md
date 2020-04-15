---
title: マッピングを行う |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLGetConnectOption
- SQLGetConnectOption function [ODBC], mapping
ms.assetid: e3792fe4-a955-473a-a297-c1b2403660c4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8d2905bd6793d032e485183c8f553cef2cdefda3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302003"
---
# <a name="sqlgetconnectoption-mapping"></a>SQLGetConnectOption のマッピング
アプリケーションが ODBC *3.x*ドライバーを使用して**SQLGetConnectOption**を呼び出すと、次の  
  
```  
SQLGetConnectOption(hdbc, fOption, pvParam)   
```  
  
 は次のようにマップされます。  
  
-   *fOption*が文字列を返す ODBC 定義の接続オプションを示している場合、ドライバー マネージャーは、次のように呼び出します。  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   *fOption*が 32 ビット整数値を返す ODBC 定義の接続オプションを示している場合、ドライバー マネージャーは、32 ビットの整数値を呼び出します。  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   *fOption*がドライバ定義のステートメント オプションを示す場合、ドライバー マネージャーは  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 前の 3 つのケースでは、*引数の引数*が*hdbc*の値に設定され、 *Attribute*引数は*fOption*の値に設定され *、ValuePtr*引数は*pvParam*と同じ値に設定されます。  
  
 ODBC 定義の文字列の接続文字列オプションの場合、ドライバー マネージャーは **、SQLGetConnectAttr**の呼び出しで*BufferLength*引数を定義済みの最大長 (SQL_MAX_OPTION_STRING_LENGTH) に設定します。文字列以外の接続文字列オプションの場合 *、BufferLength*は 0 に設定されます。  
  
 ODBC *3.x*ドライバの場合、ドライバ マネージャは、*オプション*がSQL_CONN_OPT_MINとSQL_CONN_OPT_MAXの間にあるか、またはSQL_CONNECT_OPT_DRVR_STARTより大きいかどうかをチェックしなくなりました。 ドライバーは、オプションの値の有効性を確認する必要があります。
