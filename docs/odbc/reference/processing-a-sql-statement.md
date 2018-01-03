---
title: "SQL ステートメントの処理 |Microsoft ドキュメント"
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
helpviewer_keywords:
- sending SQL statements to DBMS [ODBC]
- SQL statements [ODBC], processing
- SQL [ODBC], processing statements
- statement processing [ODBC]
- SQL statements [ODBC]
- ODBC [ODBC], SQL
ms.assetid: 96270c4f-2efd-4dc1-a985-ed7fd5658db2
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: aaf3c1fddb673e0cd62d334e9b87eeb2d9016ec6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="processing-a-sql-statement"></a>SQL ステートメントの処理
プログラムによる SQL を使用する方法を説明する前に、SQL ステートメントを処理する方法について説明する必要があります。 必要な手順は、各方法に異なるタイミングで実行が次の 3 つの方法がすべてに必要な場合に共通です。 次の図では、このセクションの残りの部分で説明する SQL ステートメントの処理に関連した手順を示します。  
  
 ![SQL ステートメントを処理するための手順](../../odbc/reference/media/pr01.gif "pr01")  
  
 SQL ステートメントを処理するには、DBMS は、次の 5 つの手順を実行します。  
  
1.  DBMS は、まず、SQL ステートメントを解析します。 これは、ステートメントをトークンと呼ばれる、個々 の単語に分割、有効な動詞と有効な句というように、ステートメントを持つことを確認します。 このステップでは、構文エラーおよびスペル ミスを検出できます。  
  
2.  DBMS では、ステートメントを検証します。 システム カタログに対してこのステートメントを確認します。 ステートメントで指定されたすべてのテーブルに、データベースにも存在しますか。 すべての列が存在するあいまいな列の名前がありません. ステートメントの実行に必要な特権があるか。 このステップでは、特定のセマンティック エラーを検出できます。  
  
3.  DBMS には、ステートメントのアクセス プランが生成されます。 アクセスの計画は、ステートメントを実行するために必要な手順のバイナリ表現です。実行可能コードの DBMS に相当することをお勧めします。  
  
4.  DBMS は、アクセス プランが最適化されます。 アクセスの計画を実行するさまざまな方法を説明します。 検索を高速にインデックスを使用できますか。 必要があります、DBMS はまずテーブル A に検索条件を適用して、テーブル B に参加させますまたは必要があります、で始め、結合後で、検索条件を使用しますか。 テーブルを順次検索を回避したり、テーブルのサブセットに縮小しますか。 その他の方法を学習した後は、DBMS は、それらのいずれかを選択します。  
  
5.  DBMS では、アクセスの計画を実行して、ステートメントを実行します。  
  
 データベースへのアクセスが必要として、必要な時間の量の量、SQL ステートメントを処理するための手順が異なります。 SQL ステートメントを解析し、データベースへのアクセスをしないため、非常に迅速に行うことができます。 その一方は、CPU を大量に消費、最適化を処理し、システム カタログへのアクセスが必要です。 だけで複雑なクエリでは、オプティマイザーは何千もの同じクエリを実行するさまざまな方法を調べることがあります。 ただし、効率的でないクエリを実行するコストは非常に高いため、最適化に要した時間が増加したクエリの実行速度の回復は、複数のでは通常です。 これは、反復的なクエリを実行する同じのアクセスを最適化プランを繰り返し使用できる場合、さらに大きなです。
