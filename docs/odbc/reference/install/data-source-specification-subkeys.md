---
title: データ ソース仕様サブキー |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data source specification subkeys [ODBC]
- registry entries for data sources [ODBC], data source specification subkeys
- subkeys [ODBC], data source specification subkeys
ms.assetid: d7e88a07-e6ab-4258-a45d-1ca21234fbec
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 281377c307f3f3750e87bf5dc988beb7660067af
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300342"
---
# <a name="data-source-specification-subkeys"></a>データ ソースの仕様のサブキー
ODBC データ ソース サブキーに一覧表示される各データ ソースには、独自のサブキーがあります。 このサブキーは、ODBC データ ソース サブキーの下の対応する値と同じ名前です。 このサブキーの値には、ドライバー DLL が一覧表示され、データ ソースの説明が表示される場合があります。 ドライバがトランスレータをサポートしている場合、値にはデフォルトのトランスレータの名前、デフォルトの翻訳 DLL、デフォルトの翻訳オプションが表示されることがあります。 値には、データ ソースに接続するためにドライバーが必要とするその他の情報も一覧表示されます。 たとえば、ドライバーは、サーバー名、データベース名、またはスキーマ名を必要があります。  
  
 値の形式は、次の表に示すとおりです。 必要なのは、ドライバの値だけです。  
  
|名前|データ型|Data|  
|----------|---------------|----------|  
|説明|REG_SZ|*説明*|  
|Driver|REG_SZ|*ドライバ DLL パス*|  
|トランスレーションDLL|REG_SZ|*トランスレータ -DLL パス*|  
|翻訳名|REG_SZ|*翻訳者名*|  
|翻訳オプション|REG_SZ|*翻訳オプション*|  
|*オプトバリュー名*|*オプト値タイプ*|*オプトバリューデータ*|  
  
 たとえば、SQL Server ドライバが、OEM から ANSI への変換に関するサーバー名とフラグを必要とし、これらに対してサーバーと OEMTOANSI の値を定義するとします。 また、インベントリ データ ソースでは、Microsoft ® コード ページトランスレータを使用して、Windows ®ラテン 1 (1250) と多言語 (850) のコード ページ間で翻訳を行う場合を考えます。 インベントリ サブキーの下の値は次のようになります。  
  
```  
Description : REG_SZ : Inventory database on server InvServ  
Driver : REG_SZ : C:\WINDOWS\SYSTEM32\SQLSRV32.DLL  
OEMTOANSI : REG_SZ : Yes  
Server : REG_SZ : InvServ  
TranslationDLL : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
TranslationName : REG_SZ : MS Code Page Translator  
TranslationOption : REG_SZ : 12500850  
```
