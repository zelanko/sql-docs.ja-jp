---
title: ODBC トランスレーター サブキー |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
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
ms.openlocfilehash: 03c6174d69fbe7a891e35e61a208b81bdb9cc4a2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915097"
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
