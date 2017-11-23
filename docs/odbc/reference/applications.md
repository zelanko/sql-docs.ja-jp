---
title: "アプリケーション |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- off-the-shelf applications [ODBC]
- ODBC architecture [ODBC], applications
- shrink-wrapped applications [ODBC]
- application development [ODBC], types
- custom applications [ODBC]
- virtual applications [ODBC]
- generic applications [ODBC]
ms.assetid: 39d6461f-0d24-4b7d-a723-843ade15ad73
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 07ea2d2f08fb0d31ed141281b195742462350a5b
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="applications"></a>[アプリケーション]
*アプリケーション*データにアクセスする、ODBC API を呼び出すプログラムです。 可能なさまざま種類のアプリケーションが、ほとんどは、このガイドで説明する例として使用されている 3 つのカテゴリに分類されます。  
  
-   **汎用アプリケーション**シュリンク ラップされたアプリケーションまたは既製のアプリケーションと呼びますこれらもします。 汎用アプリケーションは、さまざまな Dbms のさまざまなを使用する設計されています。 例として、スプレッドシートまたはさらなる分析データをインポートする ODBC を使用する統計パッケージや ODBC を使用してデータベースからメーリング リストを取得する、ワード プロセッサです。  
  
     汎用アプリケーションの重要なサブカテゴリは、PowerBuilder、Microsoft® Visual Basic® などのアプリケーションの開発環境です。 これらの環境で構築されたアプリケーションは、おそらく 1 つのデータベース管理システムでのみ動作、環境自体では、複数の Dbms を使用する必要があります。  
  
     どのような汎用のすべてのアプリケーションが共通のされている高 Dbms の間で同時には、比較的一般的な方法では ODBC を使用する必要があります。 相互運用性に関する詳細については、次を参照してください。 [、レベルの相互運用性を選択する](../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md)です。  
  
-   **垂直方向アプリケーション**垂直方向のアプリケーションが注文エントリや製造データの追跡などのタスクの 1 つの種類を実行して、アプリケーションの開発者によって制御されるデータベース スキーマを使用します。 特定の顧客のアプリケーションは、1 つの DBMS とします。 たとえば、スモール ビジネス可能性がありますでアプリケーションを使用 dBase 中、大企業で Oracle を使用することができます。  
  
     アプリケーションは、限られた数の同様の機能を提供する Dbms に関連付けることがありますが、アプリケーションは、1 つの DBMS に関連付けられていない方法で ODBC を使用します。 したがって、アプリケーション開発者は、DBMS から独立してアプリケーションを販売できます。 これらは、開発します、に顧客を選択する DBMS noninteroperable コードを含めることがありますが変更される時に、垂直方向のアプリケーションを使用することが相互運用可能です。  
  
-   **カスタム アプリケーション**カスタム アプリケーションが 1 つの会社で、特定のタスクを実行するために使用します。 たとえば、大企業でのアプリケーションは、(それぞれを使用してさまざまな DBMS) 複数の部門からの売上データを収集し、1 つのレポートを作成することがします。 共通のインターフェイス、なくなりますプログラマを複数のインターフェイスを参照してください。 ODBC が使用されます。 このようなアプリケーションでは、相互運用可能なは一般的に、特定の Dbms とドライバーに書き込まれます。  
  
 タスクの数は、ODBC の使用方法に関係なく、すべてのアプリケーションに共通です。 まとめると、ほぼ定義、ODBC アプリケーションのフローします。 タスクは次のとおりです。  
  
-   データ ソースを選択しに接続します。  
  
-   実行のため、SQL ステートメントを送信しています。  
  
-   (存在する場合) は、結果を取得しています。  
  
-   エラーを処理しています。  
  
-   コミットまたは SQL ステートメントの外側のトランザクションをロールバックします。  
  
-   データ ソースからの接続を切断します。  
  
 SQL を使用した、ほとんどのデータにアクセスする作業が行われるために、アプリケーションが ODBC を使用する主なタスクは SQL ステートメントを送信し、これらのステートメントによって生成された結果 (存在する場合) を取得するです。 アプリケーションが ODBC を使用するその他のタスクには、特定しドライバーの機能を調整して、データベース カタログの参照が含まれます。
