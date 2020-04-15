---
title: ODBC サブキー |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 96e9a5f4c3cdac5097686528d3c089d9ec5826f7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287442"
---
# <a name="odbc-subkey"></a>ODBC のサブキー
ODBC サブキーの下の値は、ODBC トレース オプションを指定します。 これらのオプションは、 **SQLManageDataSources**によって表示される [ODBC データ ソース アドミニストレータ] ダイアログ ボックスの [トレース] タブで設定します。 ODBC サブキー自体はオプションです。 これらの値の形式は、次の表に示すとおりです。  
  
|名前|データ型|Data|  
|----------|---------------|----------|  
|Trace|REG_SZ|**0** &#124; **1**|  
|TraceFile|REG_SZ|*トレースファイルパス*|  
  
 値には、次の表で説明する意味があります。  
  
|[値]|意味|  
|-----------|-------------|  
|Trace|アプリケーションが SQL_HANDLE_ENV オプションを指定して**SQLAllocHandle**を呼び出したときにトレース値が 1 に設定されている場合、トレースは呼び出し元のアプリケーションで有効になります。<br /><br /> アプリケーションが SQL_HANDLE_ENV オプションを指定して**SQLAllocHandle**を呼び出したときに Trace キーワードが 0 に設定されている場合、トレースは呼び出し元のアプリケーションに対して無効になります。 これが既定値です。<br /><br /> アプリケーションは、SQL_ATTR_TRACE接続属性を使用してトレースを有効または無効にできます。 ただし、この場合、この値のデータは変更されません。|  
|TraceFile|トレースが有効になっている場合、ドライバー マネージャーは、TraceFile 値で指定されたトレース ファイルに書き込みます。<br /><br /> トレース ファイルが指定されていない場合、ドライバー マネージャーは、現在のドライブ上の Sql.log ファイルに書き込みます。 これが既定値です。<br /><br /> トレースは、単一のアプリケーションに対してのみ使用するか、各アプリケーションで異なるトレース ファイルを指定する必要があります。 そうしないと、複数のアプリケーションが同じトレース ファイルを同時に開こうとし、エラーが発生します。<br /><br /> アプリケーションは、SQL_ATTR_TRACEFILE接続属性を使用して新しいトレース ファイルを指定できます。 ただし、この場合、この値のデータは変更されません。|  
  
 たとえば、トレースが有効で、トレース ファイルが C:\Odbc.log であるとします。 ODBC サブキーの下の値は次のようになります。  
  
```  
Trace : REG_SZ : 1  
TraceFile : REG_SZ : C:\ODBC.LOG  
  
```
