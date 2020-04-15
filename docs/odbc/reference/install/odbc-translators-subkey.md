---
title: ODBC トランスレータ サブキー |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 617416adfcddfbf041c48acbf83cb9589e34ae27
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296222"
---
# <a name="odbc-translators-subkey"></a>ODBC トランスレーターのサブキー
ODBC トランスレータ サブキーの下の値には、インストールされているトランスレータが一覧表示されます。 これらの値の形式を次の表に示します。  
  
|名前|データ型|Data|  
|----------|---------------|----------|  
|*翻訳者-desc*|REG_SZ|**インストール済み**|  
  
 *トランスレータ-desc*名は、トランスレータ開発者によって定義されます。  
  
 たとえば、あるユーザーが Microsoft ® コード ページトランスレータとカスタム ASCII を EBCDIC トランスレータにインストールしたとします。 ODBC トランスレータ サブキーの下の値は次のようになります。  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
