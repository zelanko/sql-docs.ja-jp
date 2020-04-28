---
title: ODBC トランスレーターサブキー |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81296222"
---
# <a name="odbc-translators-subkey"></a>ODBC トランスレーターのサブキー
[ODBC トランスレーター] サブキーの下の値には、インストールされている翻訳者が一覧表示されます。 これらの値の形式を次の表に示します。  
  
|名前|データの種類|データ|  
|----------|---------------|----------|  
|*変換プログラム-desc*|REG_SZ|**インストール済み**|  
  
 *翻訳者 desc*の名前は、translator 開発者によって定義されます。  
  
 たとえば、ユーザーが Microsoft®コードページ変換プログラムをインストールしているとします。また、カスタム ASCII to EBCDIC translator がインストールされているとします。 ODBC トランスレーターサブキーの下の値は、次のようになります。  
  
```  
MS Code Page Translator: REG_SZ : Installed  
ASCII to EBCDIC: REG_SZ : Installed.  
```
