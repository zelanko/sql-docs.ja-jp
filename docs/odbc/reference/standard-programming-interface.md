---
title: 標準プログラミングインタフェース |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], programming interface
- programming interface standardization [ODBC]
ms.assetid: a2fa727e-51f2-4123-ae25-0ee28e611231
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c7767f113d0f70569ce253f0200cd35cb83915a4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81279998"
---
# <a name="standard-programming-interface"></a>標準のプログラミング インターフェイス
プログラミング・インターフェースは、おそらく標準化の最も明白な候補です。 実際、ODBC が開発された時点では、ANSI と ISO は既に組み込み SQL モジュールと SQL モジュールの標準を提供していました。 データベース CLI に対する標準は存在しませんが、データベース ベンダの業界コンソーシアムである SQL Access Group は、データベース ベンダの標準を作成するかどうかを検討していました。ODBC の一部は、後に彼らの作業の基礎となりました。  
  
 ODBC の要件の 1 つは、1 つのアプリケーション バイナリが複数の Dbms で動作する必要があったということです。 このため、ODBC は組み込み SQL 言語やモジュール言語を使用しません。 組み込み SQL 言語およびモジュール言語の言語は標準化されていますが、それぞれ DBMS 固有のプリコンパイラーに関連付けられています。 したがって、アプリケーションは DBMS ごとに再コンパイルする必要があり、結果のバイナリは 1 つの DBMS でのみ動作します。 これは、ミニコンピュータやメインフレームの世界で見られる少量のアプリケーションでは許容できますが、パーソナルコンピュータの世界では受け入れられません。 第一に、大量のシュリンクラップされたソフトウェアの複数のバージョンを顧客に提供することは、物流上の悪夢です。第二に、パーソナル・コンピュータ・アプリケーションは、複数のDBMSに同時にアクセスする必要がしばしばあります。  
  
 一方、呼び出しレベルのインターフェイスは、各ローカル コンピューター上に存在するライブラリまたはデータベース ドライバーを通じて実装できます。DBMS ごとに異なるドライバが必要です。 最新のオペレーティング システムでは、実行時にこのようなライブラリ (Microsoft® Windows® オペレーティング システムのダイナミック リンク ライブラリなど) を読み込むことができるため、1 つのアプリケーションは、再コンパイルせずに異なる DBMS のデータにアクセスでき、また複数のデータベースから同時にデータにアクセスできます。 新しいデータベース ドライバが利用可能になると、ユーザーはデータベース アプリケーションを変更、再コンパイル、または再リンクしなくても、コンピュータにインストールできます。 さらに、ODBC が開発されたプラットフォームである Windows が既にこのようなライブラリを使用しているため、呼び出しレベルのインターフェイスは ODBC の候補として適しています。
