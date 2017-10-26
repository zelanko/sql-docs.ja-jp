---
title: "SQLSetConnectOption マッピング |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLSetConnectOption function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLSetConnectOption
ms.assetid: a1b325cf-0c42-41c1-b141-b5a4fee7e708
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e531888390bbe4f625d308ad983059634e84ba2b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetconnectoption-mapping"></a>SQLSetConnectOption マッピング
ODBC 2 時にします。*x*アプリケーション呼び出し**SQLSetConnectOption**から ODBC 3*.x*ドライバーへの呼び出し  
  
```  
SQLSetConnectOption(hdbc, fOption, vParam)  
```  
  
 次のようになります。  
  
-   場合*fOption*文字列、ドライバー マネージャーの呼び出しを必要とする接続の ODBC で定義された属性を示します  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, SQL_NTS)  
    ```  
  
-   場合*fOption*ドライバー マネージャーの呼び出し、32 ビット整数値を返す ODBC で定義された接続属性を示します  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, 0)  
    ```  
  
-   場合*fOption*ドライバーの定義済みの接続属性、ドライバー マネージャーの呼び出しを示します  
  
    ```  
    SQLSetConnectAttr(ConnectionHandle, Attribute, ValuePtr, BufferLength)  
    ```  
  
 上記の 3 つのケースで、 *ConnectionHandle*引数の値に設定されて*hdbc*、*属性*引数の値に設定されて*fOption*、および*ValuePtr*引数と同じ値に設定されて*vParam*です。  
  
 有効な値で渡す必要がある、ドライバー マネージャーが、文字列または 32 ビット整数値に、ドライバーの定義済みの接続属性が必要かどうかを把握していないため、 *BufferLength*の引数**SQLSetConnectAttr**. 特別な意味を定義しているドライバー場合ドライバーの定義済み接続属性を使用して呼び出す必要があります**SQLSetConnectOption**、サポートする必要がある必要があります**SQLSetConnectOption**です。  
  
 ODBC 2 場合。*x*アプリケーション呼び出し**SQLSetConnectOption**オプションを設定する、ドライバー固有のステートメントで ODBC 3*.x*ドライバー、およびオプションは、ODBC 2 で定義されました*。x* ODBC 3 のオプションのドライバー、新しいマニフェスト定数のバージョンを定義する必要があります*.x*ドライバー。 呼び出しで、古いマニフェスト定数が使用されている場合**SQLSetConnectOption**、ドライバー マネージャーが呼び出す**SQLSetConnectAttr**で、 **StringLength**引数を 0 に設定されています。  
  
 ODBC 3*.x*ドライバー、ドライバー マネージャーがチェックされなくなるかどうかを*fOption* SQL_CONN_OPT_MIN と SQL_CONN_OPT_MAX、間、または SQL_CONNECT_OPT_DRVR_START よりも大きいです。  
  
## <a name="setting-statement-options-on-the-connection-level"></a>接続レベルのステートメントのオプションを設定  
 ODBC 2 です。*x*、アプリケーションが呼び出し**SQLSetConnectOption**ステートメント オプションを設定します。 ドライバーがステートメントのオプションを既定としてを確立するインストールが完了したら、その接続に割り当てられた後ですべてのステートメント。 ドライバーで定義されて、ドライバーがすべて既存ステートメントで指定した接続に関連付けられているステートメント オプションを設定するかどうか。  
  
 ODBC 3 でこの機能は廃止されて*.x*です。 ODBC 3*.x*ドライバーのみをサポートする必要 ODBC 2 を設定します*。x* ODBC 2 を使用する場合は、接続レベルでのステートメント属性*。x*これを実行するアプリケーション。 ODBC 3*.x*アプリケーションは、接続レベルでステートメント属性を設定しない必要があります。 ODBC 3*.x*を除き、SQL_ATTR_METADATA_ID と SQL_ATTR_ASYNC_ENABLE 属性接続属性とステートメント属性の両方が可能であり、接続レベルでのステートメント属性を設定することはできません接続のレベルまたはステートメント レベルのいずれかに設定します。

