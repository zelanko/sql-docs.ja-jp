---
title: "ODBC とは何ですか。 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ODBC [ODBC], about ODBC
ms.assetid: badf3a45-f941-44ae-a31d-393116f68a18
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: f1cb1869039572d0d6da1302f66ce64abc3f2590
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="what-is-odbc"></a>ODBC とは何ですか。
コンピューティングの世界で ODBC に関する多くの誤解が存在します。 エンド ユーザーには、Microsoft® Windows® のコントロール パネルのアイコンです。 アプリケーション プログラマは、データ アクセスのルーチンを含むライブラリを勧めします。 他の多くには、想像れたすべてのデータベース アクセスの問題に対する回答を勧めします。  
  
 第一に、ODBC、データベース API の仕様です。 この API は、1 つの DBMS やオペレーティング システムに関係なく、します。このマニュアルでは、C では、言語に依存しないとは ODBC API です。 ODBC API は、Open Group および ISO/IEC から CLI 仕様に基づいています。 ODBC 3 です。*x*完全にこれらの仕様の両方を実装して、以前のバージョンの ODBC がこれらの仕様の予備バージョンに基づいて作成されたが、実装されていない完全に — スクリーン ベースの開発者によって一般に必要な機能が追加されてスクロール可能なカーソルなどのデータベース アプリケーション。  
  
 ODBC API の関数は、DBMS 固有のドライバーの開発者によって実装されます。 アプリケーションは、DBMS に依存しない方法でデータにアクセスするこれらのドライバーで関数を呼び出します。 ドライバー マネージャーは、アプリケーションやドライバーの間の通信を管理します。  
  
 Microsoft では、Microsoft Windows® 95 を実行しているコンピューターのドライバー マネージャーを提供し、後が書き込まれるいくつかの ODBC ドライバー、および ODBC 関数の呼び出しからそのアプリケーションの一部は、ODBC アプリケーションやドライバーだれでも記述できます。 実際には、現在、ODBC アプリケーションと使用可能なドライバーの大部分は Microsoft 以外の会社で記述されます。 さらに、ODBC ドライバーとアプリケーション、Macintosh® とさまざまな UNIX プラットフォーム上に存在します。  
  
 アプリケーションおよびドライバーの開発者のために、マイクロソフトは、ODBC ソフトウェア開発キット (SDK) Windows 95 が実行しているコンピューターを提供し、後で、ドライバー マネージャー、インストーラー DLL、テスト ツール、およびサンプル アプリケーションを提供します。 Microsoft に移植するこれらの Sdk、Macintosh や UNIX プラットフォームのさまざまなを Visigenic ソフトウェアと提携しています。  
  
 ODBC がデータベースの機能を公開するありませんこれらを補足するものに設計されているかを理解しておく必要があります。 したがって、アプリケーションの作成者では、ODBC を使用してが突然変換する単純なデータベースを完全に機能を備えたのリレーショナル データベース エンジンには限りません。 また、ドライバーの作成者は、基になるデータベースに含まれない機能を実装するが必要です。 この例外は、ファイル データ (ファイルのデータを Xbase) などに直接アクセスするドライバーを記述する開発者が最低限の SQL 機能をサポートするデータベース エンジンを書き込みに必要なことです。 別の例外は、以前に、Microsoft Data Access Components (MDAC) SDK 含まれている、Windows SDK の ODBC コンポーネントは、特定のレベルの機能を実装するドライバーのスクロール可能なカーソルをシミュレートするカーソル ライブラリを提供です。  
  
 ODBC を使用するアプリケーションでは、データベース間の機能をすべてを担当します。 たとえば、ODBC が異種結合エンジンもありません分散トランザクション プロセッサ。 ただし、これは、DBMS に依存しないであるために、このようなデータベースにまたがるツールを構築する使用できます。
