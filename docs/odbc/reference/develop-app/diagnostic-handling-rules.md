---
title: "処理規則診断 |Microsoft ドキュメント"
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
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], diagnostic handling rules
- SQLGetDiagRec function [ODBC], diagnostic handling rules
- diagnostic information [ODBC], SqlGetDiagRec
ms.assetid: 74387c3a-d6b3-4c35-b209-b9612602b20a
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d7dde3b01f27efb992640594d46756b38cb94ede
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="diagnostic-handling-rules"></a>診断の処理ルール
次の規則は、処理、診断**SQLGetDiagRec**と**SQLGetDiagField**です。  
  
 すべての ODBC コンポーネント。  
  
-   必要がありますいないを交換して、変更、またはエラーまたは警告が別の ODBC コンポーネントから受信したをマスクします。  
  
-   別の ODBC コンポーネントから、診断メッセージを受信したときに、追加の状態レコードを追加できます。 追加されたレコードは、元のメッセージに対する実際の情報の値を追加する必要があります。  
  
 ODBC のコンポーネントは、データ ソースを直接インターフェイスします。  
  
-   その仕入先識別子、そのコンポーネントの識別子およびデータ ソースから受信する診断メッセージをデータ ソースの識別子を付ける必要があります。  
  
-   データ ソースのネイティブ エラー コードを保持する必要があります。  
  
-   データ ソースの診断メッセージを保持する必要があります。  
  
 ODBC コンポーネントのエラーまたは警告に関係なく、データ ソースを生成します。  
  
-   エラーまたは警告の適切な SQLSTATE を指定する必要があります。  
  
-   診断メッセージのテキストを生成する必要があります。  
  
-   その仕入先 id と診断メッセージをそのコンポーネントの識別子を付ける必要があります。  
  
-   いずれかの利用可能で、意味のある場合は、ネイティブ エラー コードを返す必要があります。  
  
 ドライバー マネージャーとのインターフェイスと ODBC コンポーネント。  
  
-   出力引数を初期化する必要があります**SQLGetDiagRec**と**SQLGetDiagField**です。  
  
-   書式設定し、診断情報の出力引数としてを返す必要があります**SQLGetDiagRec**と**SQLGetDiagField**その関数が呼び出されたとき。  
  
 1 つの ODBC コンポーネント、ドライバー マネージャー以外。  
  
-   ネイティブのエラーに基づいて SQLSTATE を設定する必要があります。 ファイル ベースのドライバーとゲートウェイを使用しない DBMS に基づいたドライバーの場合は、ドライバーは SQLSTATE を設定する必要があります。 DBMS に基づいたドライバーのゲートウェイを使用する場合は、ドライバーまたは ODBC をサポートするゲートウェイのいずれかが、SQLSTATE を設定できます。
