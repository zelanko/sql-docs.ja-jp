---
title: ODBC トランスレーター サブキー |Microsoft ドキュメント
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
ms.topic: conceptual
helpviewer_keywords:
- translator subkey [ODBC]
- subkeys [ODBC], translator subkey
- registry entries for components [ODBC], translator subkey
ms.assetid: 6b170f1f-e263-4aac-9d49-8d0ca0470ca2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a6c59901d3e784f1ab845da595c84a4e74a0129
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="odbc-translators-subkey"></a>ODBC 変換者のサブキー
ODBC 変換器サブキーの下の値には、インストールされているトランスレーターが一覧表示します。 これらの値の形式は次の表に示します。  
  
|名前|データ型|Data|  
|----------|---------------|----------|  
|*トランスレーター desc*|REG_SZ|**インストールされています。**|  
  
 *トランスレーター desc*名は変換プログラムの開発者によって定義されます。  
  
 たとえば、ユーザーがインストールされている、Microsoft® コード ページ変換プログラムとカスタム ASCII EBCDIC トランスレーターとします。 ODBC 変換器サブキーの下の値は次のあります。  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
