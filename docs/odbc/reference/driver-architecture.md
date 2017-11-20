---
title: "ドライバーのアーキテクチャ |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC], architecture
ms.assetid: c5003413-0cc1-4f41-b877-a64e2f5ab118
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a74f6e1b212f570ba9aa47a09310b63b13ee0e42
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="driver-architecture"></a>ドライバーのアーキテクチャ
ドライバーのアーキテクチャは、どのソフトウェア プロセス SQL ステートメントによって、2 つのカテゴリに分類されます。  
  
-   **ファイル ベースのドライバー**ドライバーは、物理的なデータを直接アクセスします。 ドライバーがドライバーとデータ ソースの両方として機能するこの例では、つまり、ODBC の呼び出しと SQL ステートメントを処理します。 たとえば、dBASE ドライバーは、dBASE はスタンドアロン データベース エンジン、ドライバーを使用できますを提供しないので、ドライバーのファイル ベースです。 ファイル ベースのドライバーの開発者が独自のデータベース エンジンを書き込む必要がありますに注意してくださいに重要です。  
  
-   **DBMS に基づいたドライバー**ドライバーを別のデータベース エンジンを介して物理データにアクセスします。 ここではドライバーが; ODBC 呼び出しのみを処理します。SQL ステートメントに渡すには、データベース エンジンを処理します。 たとえば、Oracle のドライバーは、Oracle のドライバーを使用してスタンドアロン データベース エンジンのため、DBMS に基づいたドライバーです。 データベース エンジンが存在するではありません。 ドライバーと同じコンピューターまたはネットワーク上の別のマシン上に存在できることゲートウェイを経由でもアクセス可能性があります。  
  
 一般に、ドライバーの作成者にのみ興味深いは、ドライバーのアーキテクチャつまり、ドライバーのアーキテクチャ一般にも違いはありません、アプリケーションにします。 ただし、アプリケーションは、DBMS に固有の SQL を使用できるかどうか、アーキテクチャに影響します。 たとえば、Microsoft Access では、スタンドアロン データベース エンジンを提供します。 Microsoft Access ドライバーは、DBMS に基づいた場合、このエンジンを通じてデータにアクセスする — アプリケーションが Microsoft Access – SQL ステートメントを処理エンジンに渡すことができます。  
  
 ただし場合は、ドライバーでは、ファイル ベース — は、Microsoft® Access .mdb ファイルに直接アクセスする独自のエンジンが含まれている — しようとした Microsoft Access 固有の SQL ステートメントをエンジンに渡しますが構文エラーが発生する可能性があります。 理由は、エンジン専用が ODBC SQL のみを実装する可能性が高いことです。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [ファイル ベースのドライバー](../../odbc/reference/file-based-drivers.md)  
  
-   [DBMS に基づいたドライバー](../../odbc/reference/dbms-based-drivers.md)  
  
-   [ネットワークの例](../../odbc/reference/network-example.md)  
  
-   [他のドライバーのアーキテクチャ](../../odbc/reference/other-driver-architectures.md)

