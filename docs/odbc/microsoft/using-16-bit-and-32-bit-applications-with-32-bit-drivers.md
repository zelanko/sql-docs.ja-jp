---
title: "16 ビットおよび 32 ビット アプリケーションを使用して、32 ビット ドライバーが |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC drivers [ODBC], 16-bit applications
- ODBC drivers [ODBC], 32-bit applications
- 32-bit applications with 32-bit drivers [ODBC]
- 16-bit applications with 32-bit drivers [ODBC]
ms.assetid: fc65c988-b31f-4cc9-851f-30d2119604fd
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 802b09dd83ce3671edbff33ff2be447c6279621f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-16-bit-and-32-bit-applications-with-32-bit-drivers"></a>32 ビット ドライバーで 16 ビットおよび 32 ビット アプリケーションを使用
> [!IMPORTANT]  
>  16 ビット アプリケーションのサポートは、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに 32 ビットまたは 64 ビット アプリケーションを開発します。  
  
 ODBC データ アクセス コンポーネントを 16 ビットおよび 32 ビットのアプリケーションと 32 ビット ドライバーを使用できます。 Microsoft® Windows® 95/98 および Windows または Windows 2000 オペレーティング システムでは、次のアプリケーションやドライバーの組み合わせをサポートします。  
  
-   16 ビット アプリケーションと 32 ビット ドライバー  
  
-   32 ビット ドライバーが 32 ビット アプリケーション  
  
 16 ビット ドライバーを使用して、32 ビット アプリケーションを使用することはサポートされていません。  
  
> [!NOTE]  
>  以降、ODBC version 3.0 のリリースでは、Windows NT 4.0 がサポートされています。  
  
 ODBC には、「サンク」ダイナミック リンク ライブラリ (Dll) に 16 ビットのアドレスを 32 ビットのアドレスに変換およびその逆の場合は、上記の構成をサポートするために必要な ODBC コンポーネントが含まれています。 セットアップ プログラムを使用しているし、そのシステムに必要な ODBC コンポーネントをインストールするオペレーティング システムを決定します。 すべてのシステムで使用される ODBC コンポーネントをインストールすることもできます。  
  
 ほとんどの場合、アプリケーションまたはドライバーから 16 ビットの移植を 32 ビットは、5 つの種類の変更。  
  
-   メッセージの処理コードへの変更  
  
-   整数およびハンドルは、32 ビットを変更します。  
  
-   Windows アプリケーション プログラミング インターフェイス (Api) への呼び出しでの変更  
  
-   スレッド セーフ ドライバーをようにへの変更  
  
-   ODBC コンポーネントへの変更  
  
 16 ビットおよび 32 ビットの ODBC コンポーネントの主要な違いは、アプリケーションまたはドライバー プログラミングの観点には別のファイル名があることです。 システムの観点から、各アプリケーションまたはドライバーの接続のアーキテクチャが異なるとデータ ソースの管理に使用できるツールが異なります。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [32 ビット ドライバーで 16 ビット アプリケーションを使用](../../odbc/microsoft/using-16-bit-applications-with-32-bit-drivers.md)  
  
-   [32 ビット ドライバーが 32 ビット アプリケーションを使用します。](../../odbc/microsoft/using-32-bit-applications-with-32-bit-drivers.md)

