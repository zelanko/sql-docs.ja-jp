---
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
ms.openlocfilehash: a790ace40aa31324ce8b22127d8f6948ae86e059
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82764763"
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Visual C++ アプリケーションで ADO ライブラリを参照する
Visual C++ アプリケーションで最新バージョンの ADO を使用するには、次のディレクティブを使用し `#import` ます。  
  
```cpp
#import "msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
```  
  
 ADO MD または ADOX を使用するには、上記の構文を使用して*msadomd*または*msadox .dll*をインポートする必要があります。  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 以前のバージョンの ADO を使用するには、上記の*msado15.dll*を次のタイプライブラリのいずれかに置き換えます。  
  
-   *msado27*、ADO 2.7 タイプライブラリ  
  
-   *msado26*、ADO 2.6 タイプライブラリ  
  
-   *msado25*、ADO 2.5 タイプライブラリ  
  
-   *msado21*、ADO 2.1 タイプライブラリ  
  
-   *msado20*、ADO 2.0 タイプライブラリ
