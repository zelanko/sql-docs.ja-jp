---
title: "DBMS に基づいたドライバー |Microsoft ドキュメント"
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
- drivers [ODBC], DBMS-based drivers
- DBMS-based drivers [ODBC]
- ODBC architecture [ODBC], drivers
ms.assetid: e2208ee0-4cd6-4f0d-bb71-a0b54f7d9330
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7b806f4c887af3f1ba80ee3321820e97dd336fad
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="dbms-based-drivers"></a>DBMS に基づいたドライバー
DBMS に基づいたドライバーは、ドライバーを使用するためのスタンドアロン データベース エンジンを提供する Oracle または SQL Server などのデータ ソースで使用されます。 これらのドライバー、スタンドアロンのエンジンです。 物理データにアクセスします。つまり、SQL ステートメントを送信し、エンジンから結果を取得します。  
  
 DBMS に基づいたドライバーでは、既存のデータベース エンジンを使用するためには、通常より簡単に記述ファイル ベースのドライバーは。 ネイティブの API 呼び出しに ODBC 呼び出しを変換することによって、DBMS に基づいたドライバーを簡単に実装できる、このドライバーでは低速結果します。 DBMS に基づいたドライバーを実装する優れた方法としてでは、ネイティブの API の動作は通常、基になるデータ ストリーム プロトコルを使用します。 たとえば、SQL Server ドライバーでは、Db-library (SQL Server のネイティブの API) ではなく TDS (データ ストリーム プロトコル for SQL Server) を使用する必要があります。 この規則の例外は、ODBC がネイティブの API の場合です。 たとえば、Watcom SQL は、スタンドアロン エンジンをアプリケーションと同じコンピューター上に存在し、ドライバーとして直接読み込まれます。  
  
 DBMS に基づいたドライバーは、データ ソースをサーバーとして機能する、クライアント/サーバーの構成でクライアントとして機能します。 ほとんどの場合、クライアント (ドライバー) とサーバー (データ ソース) 上に存在、別のコンピューターもでしたマルチタスクのオペレーティング システムを実行している同じコンピューター上に配置が。 3 番目の可能性は、*ゲートウェイ、*ドライバーとデータ ソースの間に配置します。 ゲートウェイは、別のように 1 つの DBMS の原因となるソフトウェアの一部です。 たとえば、SQL Server を使用するアプリケーションもアクセスできる DB2 データ ゲートウェイを介して、Micro Decisionware DB2;この製品は、DB2 SQL Server のように表示します。  
  
 次の図は、DBMS に基づいたドライバーの 3 つの異なる構成を示します。 最初の構成で、ドライバーとデータ ソースが同じコンピューター上に常駐します。 2 番目ので、ドライバーとデータ ソースが異なるコンピューターに存在します。 3 番目でドライバーとデータ ソースが異なるコンピューター上に存在し、ゲートウェイはさらに別のコンピューター上にあるそれらの間に配置します。  
  
 ![DBMS の 3 つの構成 &#45; ベースのドライバー](../../odbc/reference/media/pr07.gif "pr07")
