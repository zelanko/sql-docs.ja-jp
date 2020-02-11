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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 62fb1b89299af1f466e446c8adba422a841f0196
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923024"
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Visual C++ アプリケーションで ADO ライブラリを参照する
Visual C++ アプリケーションで最新バージョンの ADO を使用するには、次`#import`のディレクティブを使用します。  
  
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
