---
title: "SQLGetConnectOption マッピング |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLGetConnectOption
- SQLGetConnectOption function [ODBC], mapping
ms.assetid: e3792fe4-a955-473a-a297-c1b2403660c4
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9a1be0f632b702083f279723b74f4474c2231bb8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetconnectoption-mapping"></a>SQLGetConnectOption マッピング
アプリケーションを呼び出すと**SQLGetConnectOption**から ODBC 3*.x*ドライバーへの呼び出し  
  
```  
SQLGetConnectOption(hdbc, fOption, pvParam)   
```  
  
 次のようにマップされます。  
  
-   場合*fOption* ODBC で定義された接続オプション文字列、ドライバー マネージャーの呼び出しを返すことを示します  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
-   場合*fOption*ドライバー マネージャーの呼び出し、32 ビット整数値を返す ODBC で定義された接続オプションを示します  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0, NULL)  
    ```  
  
-   場合*fOption*ドライバー定義ステートメントのオプションでは、ドライバー マネージャーの呼び出しを示します  
  
    ```  
    SQLGetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength, NULL)  
    ```  
  
 上記の 3 つのケースで、 *ConnectionHandle*引数の値に設定されて*hdbc*、*属性*引数の値に設定されて*fOption*、および*ValuePtr*引数と同じ値に設定されて*pvParam*です。  
  
 ODBC で定義された文字列の接続オプションでは、ドライバー マネージャーの設定、 *BufferLength*への呼び出しで引数**SQLGetConnectAttr**定義済みの最大長 (SQL_MAX_OPTION_STRING_LENGTH) です。文字列以外の接続オプション、 *BufferLength*は 0 に設定します。  
  
 ODBC 3*.x*ドライバー、ドライバー マネージャーがチェックされなくなるかどうかを*オプション*SQL_CONN_OPT_MIN と SQL_CONN_OPT_MAX、間、または SQL_CONNECT_OPT_DRVR_START よりも大きいです。 ドライバーは、オプションの値の有効性をチェックする必要があります。

