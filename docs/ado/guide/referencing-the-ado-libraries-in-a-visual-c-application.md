---
title: "Visual C アプリケーションで ADO ライブラリを参照する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: "“drivers”"
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual C++ application[ADO]
- ADO, libraries
ms.assetid: d3ea12ec-bca8-48c3-af57-ce14576108c9
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3bbb3a9345c969d5d5bc038f31f7f7bc0b731c40
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="referencing-the-ado-libraries-in-a-visual-c-application"></a>Visual C アプリケーションで ADO ライブラリを参照します。
Visual C アプリケーションで ADO の最新バージョンを使用するには、次を使用`#import`ディレクティブ。  
  
```  
#import "msado15.dll" \  
    no_namespace rename("EOF", "EndOfFile")  
```  
  
 インポートする必要がありますまたはを使用する ADO MD ADOX、 *msadomd.dll*または*msadox.dll*、上記の構文を使用しています。  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 ADO の以前のバージョンを使用するのには、置換*msado15.dll*上で次のタイプ ライブラリのいずれか。  
  
-   *msado27.tlb*、ADO 2.7 タイプ ライブラリ  
  
-   *msado26.tlb*、ADO 2.6 のタイプ ライブラリ  
  
-   *msado25.tlb*、ADO 2.5 のタイプ ライブラリ  
  
-   *msado21.tlb*、ADO 2.1 のタイプ ライブラリ  
  
-   *msado20.tlb*、ADO 2.0 タイプ ライブラリ
