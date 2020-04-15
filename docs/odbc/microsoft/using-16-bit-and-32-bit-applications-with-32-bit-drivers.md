---
title: 32 ビット ドライバでの 16 ビットおよび 32 ビット アプリケーションの使用 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], 16-bit applications
- ODBC drivers [ODBC], 32-bit applications
- 32-bit applications with 32-bit drivers [ODBC]
- 16-bit applications with 32-bit drivers [ODBC]
ms.assetid: fc65c988-b31f-4cc9-851f-30d2119604fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7ce996a7c4816d4d14491e226f891904b6cf8c02
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307613"
---
# <a name="using-16-bit-and-32-bit-applications-with-32-bit-drivers"></a>32 ビット ドライバーで 16 ビットおよび 32 ビット アプリケーションを使用
> [!IMPORTANT]  
>  16 ビット アプリケーションのサポートは、今後のバージョンの Windows で削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 代わりに、32 ビットまたは 64 ビット のアプリケーションを開発します。  
  
 ODBC データ アクセス コンポーネントを使用すると、32 ビット ドライバーを使用して 16 ビットおよび 32 ビットのアプリケーションを使用できます。 Microsoft ® Windows® 95/98 および Windows NT ®/Windows 2000 オペレーティング システムでは、次のアプリケーションとドライバの組み合わせがサポートされています。  
  
-   32 ビット ドライバーを搭載した 16 ビット アプリケーション  
  
-   32 ビット ドライバーを搭載した 32 ビット アプリケーション  
  
 16 ビット ドライバーで 32 ビット アプリケーションを使用することはサポートされていません。  
  
> [!NOTE]  
>  ODBC バージョン 3.0 のリリース以降、Windows NT 4.0 がサポートされました。  
  
 ODBC には、16 ビット アドレスを 32 ビット アドレスに変換するダイナミック リンク ライブラリ (DLL) を "サンク" することで、上記の構成をサポートするために必要な ODBC コンポーネントが含まれています。 セットアップ プログラムは、使用しているオペレーティング システムを特定し、そのシステムに必要な ODBC コンポーネントをインストールします。 また、すべてのシステムで使用される ODBC コンポーネントをインストールすることもできます。  
  
 ほとんどの場合、アプリケーションまたはドライバーを 16 ビットから 32 ビットに移植するには、次の 5 種類の変更が必要です。  
  
-   メッセージ処理コードの変更点  
  
-   整数とハンドルが 32 ビットであるために変更  
  
-   Windows アプリケーション プログラミング インターフェイス (API) の呼び出しの変更  
  
-   ドライバーをスレッド セーフにするための変更  
  
-   ODBC コンポーネントの変更点  
  
 アプリケーションまたはドライバーのプログラミングの観点から見ると、16 ビットと 32 ビットの ODBC コンポーネントの主な違いは、異なるファイル名を持つということです。 システムの観点から見ると、アプリケーションまたはドライバーの接続のアーキテクチャは異なり、データ ソースの管理に使用されるツールは異なります。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [32 ビット ドライバーで 16 ビット アプリケーションを使用](../../odbc/microsoft/using-16-bit-applications-with-32-bit-drivers.md)  
  
-   [32 ビット ドライバーで 32 ビット アプリケーションを使用](../../odbc/microsoft/using-32-bit-applications-with-32-bit-drivers.md)
