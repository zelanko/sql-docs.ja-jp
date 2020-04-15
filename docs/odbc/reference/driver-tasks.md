---
title: ドライバーのタスク |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC], tasks
ms.assetid: 184c795a-c2e8-4d20-9902-12e60b2f0e45
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1b30df63a3c955d2ed074ab13649ea55c21a6da7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294202"
---
# <a name="driver-tasks"></a>ドライバーでの処理
ドライバによって実行される具体的なタスクは次のとおりです。  
  
-   データ ソースへの接続とデータ ソースからの切断。  
  
-   ドライバ マネージャで関数エラーがチェックされていないかどうかを確認しています。  
  
-   トランザクションの発生。これはアプリケーションに対して透過的です。  
  
-   実行のために SQL ステートメントをデータ ソースに送信します。 ドライバーは、ODBC SQL を DBMS 固有の SQL に変更する必要があります。これは、ODBC で定義されたエスケープ句を DBMS 固有の SQL に置き換えることに限定されることがよくあります。  
  
-   データ ソースにデータを送信し、データ ソースからデータを取得する (アプリケーションで指定されたデータ型の変換を含む)。  
  
-   DBMS 固有のエラーを ODBC SQLSTATE にマッピングしています。
