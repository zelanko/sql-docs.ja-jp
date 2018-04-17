---
title: データ ソースの仕様のサブキー |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data source specification subkeys [ODBC]
- registry entries for data sources [ODBC], data source specification subkeys
- subkeys [ODBC], data source specification subkeys
ms.assetid: d7e88a07-e6ab-4258-a45d-1ca21234fbec
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5f3080d85b2c01491d94ecb75b956d6c67bc061b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="data-source-specification-subkeys"></a>データ ソースの仕様のサブキー
ODBC データ ソースのサブキーに表示されている各データ ソースには、独自のサブキーがあります。 このサブキーは、ODBC データ ソースのサブキーの下の対応する値として同じ名前を持ちます。 このサブキーの下の値は、ドライバー DLL を一覧表示する必要があり、データ ソースの説明が表示されます。 ドライバーは、翻訳者をサポートする場合は、既定トランスレーター、デフォルト トランスレーター DLL、および既定の変換オプションの名前をリスト値可能性があります。 値は、ドライバーによってデータ ソースに接続するために必要なその他の情報も一覧表示します。 たとえば、ドライバーでは、サーバー名、データベース名、またはスキーマ名を必要があります。  
  
 値の形式は、次の表に示すようにします。 ドライバーの値のみが必要です。  
  
|名前|データ型|Data|  
|----------|---------------|----------|  
|Description|REG_SZ|*description*|  
|Driver|REG_SZ|*ドライバー DLL パス*|  
|TranslationDLL|REG_SZ|*トランスレーター DLL パス*|  
|TranslationName|REG_SZ|*翻訳者名*|  
|TranslationOption|REG_SZ|*翻訳オプション*|  
|*選択、値の名前*|*オプトイン値型*|*オプトイン値データ*|  
  
 たとえば、SQL Server のドライバーを ANSI に変換する OEM 用、サーバー名とフラグが必要ですし、これらのサーバーと OEMTOANSI の値を定義します。 インベントリのデータ ソースでは、Microsoft® コード ページ変換プログラムを使用して、Windows® Latin 1 (1250) および多言語 (850) コード ページ間で変換にもあるとします。 インベントリのサブキーの下の値は次のあります。  
  
```  
Description : REG_SZ : Inventory database on server InvServ  
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\SQLSRV32.DLL  
OEMTOANSI : REG_SZ : Yes  
Server : REG_SZ : InvServ  
TranslationDLL : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
TranslationName : REG_SZ : MS Code Page Translator  
TranslationOption : REG_SZ : 12500850  
```
