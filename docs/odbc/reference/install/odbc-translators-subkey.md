---
title: "ODBC トランスレーター サブキー |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- translator subkey [ODBC]
- subkeys [ODBC], translator subkey
- registry entries for components [ODBC], translator subkey
ms.assetid: 6b170f1f-e263-4aac-9d49-8d0ca0470ca2
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 547790398258ef250cca0331e468b8834218890e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="odbc-translators-subkey"></a>ODBC 変換者のサブキー
ODBC 変換器サブキーの下の値には、インストールされているトランスレーターが一覧表示します。 これらの値の形式は次の表に示します。  
  
|名前|データ型|data|  
|----------|---------------|----------|  
|*トランスレーター desc*|REG_SZ|**インストールされています。**|  
  
 *トランスレーター desc*名は変換プログラムの開発者によって定義されます。  
  
 たとえば、ユーザーがインストールされている、Microsoft® コード ページ変換プログラムとカスタム ASCII EBCDIC トランスレーターとします。 ODBC 変換器サブキーの下の値は次のあります。  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
