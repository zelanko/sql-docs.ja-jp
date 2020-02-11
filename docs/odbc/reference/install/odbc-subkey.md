---
title: ODBC サブキー |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- registry entries for data sources [ODBC], ODBC subkey
- subkeys [ODBC], ODBC subkey
- ODBC subkey [ODBC]
ms.assetid: f9534144-8f42-4946-b0fb-638e9dcde9c8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8aad5171b98c54aa0c4adbde1a5678e4fd953640
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093964"
---
# <a name="odbc-subkey"></a>ODBC のサブキー
Odbc サブキーの下の値は、ODBC トレースオプションを指定します。 これらのオプションは、 **Sqlmanagedatasources**ソースによって表示される [ODBC データソースアドミニストレーター] ダイアログボックスの [トレース] タブで設定します。 ODBC サブキー自体は省略可能です。 これらの値の形式を次の表に示します。  
  
|Name|データ型|データ|  
|----------|---------------|----------|  
|Trace|REG_SZ|**0** &#124; **1**|  
|TraceFile|REG_SZ|*tracefile-path*|  
  
 値には、次の表で説明する意味があります。  
  
|Value|意味|  
|-----------|-------------|  
|Trace|アプリケーションが SQL_HANDLE_ENV オプションを使用して**SQLAllocHandle**を呼び出すときにトレース値が1に設定されていると、呼び出し元のアプリケーションでトレースが有効になります。<br /><br /> アプリケーションが SQL_HANDLE_ENV オプションを指定して**SQLAllocHandle**を呼び出すときに Trace キーワードが0に設定されている場合、呼び出し元アプリケーションのトレースは無効になります。 これが既定値です。<br /><br /> アプリケーションでは、SQL_ATTR_TRACE 接続属性を使用してトレースを有効または無効にすることができます。 ただし、この設定を行っても、この値のデータは変更されません。|  
|TraceFile|トレースが有効になっている場合、ドライバーマネージャーは TraceFile 値によって指定されたトレースファイルに書き込みます。<br /><br /> トレースファイルが指定されていない場合、ドライバーマネージャーは現在のドライブの Sql .log ファイルに書き込みます。 これが既定値です。<br /><br /> トレースは、1つのアプリケーションに対してのみ使用するか、各アプリケーションで別のトレースファイルを指定する必要があります。 そうしないと、2つ以上のアプリケーションが同時に同じトレースファイルを開こうとし、エラーが発生します。<br /><br /> アプリケーションでは、SQL_ATTR_TRACEFILE 接続属性を使用して新しいトレースファイルを指定できます。 ただし、この設定を行っても、この値のデータは変更されません。|  
  
 たとえば、トレースが有効になっていて、トレースファイルが C:\ であるとします。 ODBC サブキーの下の値は次のようになります。  
  
```  
Trace : REG_SZ : 1  
TraceFile : REG_SZ : C:\ODBC.LOG  
  
```
