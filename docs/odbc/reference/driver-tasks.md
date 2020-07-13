---
title: ドライバーのタスク |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81294202"
---
# <a name="driver-tasks"></a>ドライバーでの処理
ドライバーによって実行される特定のタスクは次のとおりです。  
  
-   データソースへの接続と切断。  
  
-   ドライバーマネージャーによってチェックされていない関数エラーを確認しています。  
  
-   トランザクションの開始これは、アプリケーションに対して透過的です。  
  
-   実行用のデータソースに SQL ステートメントを送信しています。 ドライバーは、ODBC SQL を DBMS 固有の SQL に変更する必要があります。これは、多くの場合、ODBC で定義されている、DBMS 固有の SQL を使用したエスケープ句の置換に限定されます。  
  
-   データソースとの間でのデータの送受信 (アプリケーションで指定されたデータ型の変換を含む)。  
  
-   DBMS 固有のエラーを ODBC SQLSTATEs にマップしています。
