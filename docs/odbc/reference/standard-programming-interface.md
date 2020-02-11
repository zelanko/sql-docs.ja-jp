---
title: 標準プログラミングインターフェイス |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a241ea92af6c1273039cc45daab232a1fbe763a3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081839"
---
# <a name="standard-programming-interface"></a>標準のプログラミング インターフェイス
プログラミングインターフェイスは、標準化のための最も明確な候補と考えられます。 実際、ODBC を開発しているときは、embedded SQL および SQL モジュールの標準が ANSI および ISO によって既に提供されています。 データベース CLI の標準は存在しませんが、SQL アクセスグループ (データベースベンダーの業界コンソーシアム) は、データベースを作成するかどうかを検討していました。ODBC の各部分は、後で作業の基礎になりました。  
  
 ODBC の要件の1つは、1つのアプリケーションバイナリが複数の Dbms で動作する必要があることでした。 このため、ODBC では embedded SQL またはモジュール言語が使用されません。 Embedded SQL とモジュール言語の言語は標準化されていますが、それぞれが DBMS 固有の precompilers に関連付けられています。 そのため、DBMS ごとにアプリケーションを再コンパイルする必要があり、結果として得られるバイナリは1つの DBMS でしか動作しません。 これは、minicomputer とメインフレームの世界にある低ボリュームのアプリケーションでは許容されますが、パーソナルコンピューターでは使用できません。 1つ目は、大量の、縮小ラップされたソフトウェアの複数のバージョンを顧客に提供するためのロジスティックの悪夢です。2つ目は、パーソナルコンピューターアプリケーションが複数の Dbms に同時にアクセスする必要があることです。  
  
 一方、呼び出しレベルのインターフェイスは、各ローカルコンピューター上に存在するライブラリ (またはデータベースドライバー) を使用して実装できます。DBMS ごとに異なるドライバーが必要です。 最新のオペレーティングシステムは実行時にこのようなライブラリ (Microsoft® Windows®オペレーティングシステム上のダイナミックリンクライブラリなど) を読み込むことができるため、1つのアプリケーションは、再コンパイルしなくてもデータにアクセスできます。複数のデータベースを同時に実行します。 新しいデータベースドライバーが使用可能になると、ユーザーは、データベースアプリケーションの変更、再コンパイル、または再リンクを行うことなく、これらのコンピューターにインストールするだけで済みます。 さらに、odbc の場合は、呼び出しレベルのインターフェイスが最適な候補として使用されていました。 ODBC が最初に開発されたプラットフォームであり、既にそのようなライブラリを幅広く利用しています。
