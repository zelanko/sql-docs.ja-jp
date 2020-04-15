---
title: トランスレータ仕様サブキー |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- translator subkey [ODBC]
- registry entries for components [ODBC], translator specification subkeys
- translator specification subkeys [ODBC]
- subkeys [ODBC], translator specification subkeys
ms.assetid: 3c0edeee-d43a-4466-a177-bf2d2435707a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ad21943c5313edcb09aba88d45ea21132aa9757f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296042"
---
# <a name="translator-specification-subkeys"></a>ドライバーの仕様のサブキー
ODBC トランスレータ サブキーにリストされている各トランスレータには、独自のサブキーがあります。 このサブキーは、ODBC トランスレータ サブキーの下の対応する値と同じ名前になります。 このサブキーの値には、トランスレータおよびトランスレータ セットアップ DLL の完全パスと使用回数が一覧表示されます。 値の形式は、次の表に示すとおりです。  
  
|名前|データ型|Data|  
|----------|---------------|----------|  
|[変換者]|REG_SZ|*トランスレータ -DLL パス*|  
|セットアップ|REG_SZ|*DLL パスのセットアップ*|  
|使用カウント|REG_DWORD|*count*|  
  
 使用カウントの詳細については、このセクションの「[使用カウント](../../../odbc/reference/install/usage-counting.md)」を参照してください。  
  
 アプリケーションでは、使用カウントを設定しないでください。 ODBC はこのカウントを維持します。  
  
 たとえば、Microsoft コード ページトランスレータに Mscpxl32.dll という名前の翻訳 DLL があり、トランスレータのセットアップ関数が同じ DLL 内にあり、トランスレータが 3 回インストールされているとします。 Microsoft コード ページトランスレータ サブキーの下の値は次のようになります。  
  
```  
Translator : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
Setup : REG_SZ : C:\WINDOWS\SYSTEM32\MSCPXL32.DLL  
UsageCount : REG_DWORD : 0x3  
```
