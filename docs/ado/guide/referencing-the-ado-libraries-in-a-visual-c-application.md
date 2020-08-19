---
description: Visual C++ アプリケーションで ADO ライブラリを参照する
title: Visual C++ アプリケーションで ADO ライブラリを参照する |Microsoft Docs
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual C++ application[ADO]
- ADO, libraries
ms.assetid: d3ea12ec-bca8-48c3-af57-ce14576108c9
author: rothja
ms.author: jroth
ms.openlocfilehash: d71a56b6cb09924e106b62ed5bbca542cf9e797f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88452364"
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Visual C++ アプリケーションで ADO ライブラリを参照する
Visual C++ アプリケーションで最新バージョンの ADO を使用するには、次のディレクティブを使用し `#import` ます。  
  
```cpp
#import "msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
```  
  
 ADO MD または ADOX を使用するには、上記の構文を使用して *msadomd.dll* または *msadox.dll*をインポートする必要があります。  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 以前のバージョンの ADO を使用するには、上記の *msado15.dll* を次のタイプライブラリのいずれかに置き換えます。  
  
-   *msado27*、ADO 2.7 タイプライブラリ  
  
-   *msado26*、ADO 2.6 タイプライブラリ  
  
-   *msado25*、ADO 2.5 タイプライブラリ  
  
-   *msado21*、ADO 2.1 タイプライブラリ  
  
-   *msado20*、ADO 2.0 タイプライブラリ
