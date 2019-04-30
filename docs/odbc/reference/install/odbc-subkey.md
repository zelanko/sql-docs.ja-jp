---
title: ODBC のサブキー |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: ee7cf624e7c118a5d9ef36738c810aecc4ec5684
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63281009"
---
# <a name="odbc-subkey"></a>ODBC のサブキー
ODBC のサブキーの下の値は、ODBC トレース オプションを指定します。 これらのオプションを設定で表示される ODBC データ ソース アドミニストレーター ダイアログ ボックスの トレース タブから**SQLManageDataSources**します。 ODBC のサブキー自体は省略可能です。 これらの値の形式は、次の表に示すようにします。  
  
|名前|データ型|data|  
|----------|---------------|----------|  
|Trace|REG_SZ|**0** &#124; **1**|  
|TraceFile|REG_SZ|*tracefile パス*|  
  
 値には、次の表で説明されている意味があります。  
  
|値|説明|  
|-----------|-------------|  
|Trace|トレースの値が設定されている場合に 1 の場合にアプリケーションを呼び出す**SQLAllocHandle** sql_handle_env としてオプションでは、呼び出し元アプリケーションのトレースを有効にします。<br /><br /> アプリケーションを呼び出すときに、トレースのキーワードが 0 に設定されてかどうか**SQLAllocHandle** sql_handle_env としてオプションでは、呼び出し元アプリケーションのトレースが無効です。 これが既定値です。<br /><br /> アプリケーションでは、有効にしたり、SQL_ATTR_TRACE 接続属性を持つトレースを無効にすることができます。 ただし、そのように変わりませんこの値のデータ。|  
|TraceFile|トレースが有効になっている場合、ドライバー マネージャーは、トレースファイル値で指定されたトレース ファイルに書き込みます。<br /><br /> トレース ファイルが指定されていない場合、ドライバー マネージャーは、現在のドライブに Sql.log ファイルに書き込みます。 これが既定値です。<br /><br /> トレースは、1 つのアプリケーションに対してのみ使用する必要があります。 または各アプリケーションは、さまざまなトレース ファイルを指定する必要があります。 それ以外の場合、2 つまたは複数のアプリケーションはしようとすると、同時に同じトレース ファイルを開くエラーが発生します。<br /><br /> アプリケーションでは、SQL_ATTR_TRACEFILE 接続属性を持つ、新しいトレース ファイルを指定できます。 ただし、そのように変わりませんこの値のデータ。|  
  
 たとえば、トレースが可能になり、トレース ファイルは C:\Odbc.log とします。 ODBC のサブキーの下の値には、次のようになります。  
  
```  
Trace : REG_SZ : 1  
TraceFile : REG_SZ : C:\ODBC.LOG  
  
```
