---
title: ODBC トランスレーターのサブキー |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- translator subkey [ODBC]
- subkeys [ODBC], translator subkey
- registry entries for components [ODBC], translator subkey
ms.assetid: 6b170f1f-e263-4aac-9d49-8d0ca0470ca2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9e7109a6f1b88cf7639b2fc823ce0c5f14d05002
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47673240"
---
# <a name="odbc-translators-subkey"></a>ODBC トランスレーターのサブキー
ODBC トランスレーターのサブキーの下の値には、インストールされている翻訳者が一覧表示します。 これらの値の形式は、次の表に示します。  
  
|名前|データ型|data|  
|----------|---------------|----------|  
|*translator desc*|REG_SZ|**インストールされています。**|  
  
 *Translator desc*名は変換プログラムの開発者によって定義されます。  
  
 たとえば、ユーザーがインストール、Microsoft® コード ページ変換プログラムおよびカスタムの ASCII EBCDIC トランスレーターとします。 ODBC トランスレーターのサブキーの下の値は、次のようにあります。  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
