---
description: ドライバーでの処理
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
ms.openlocfilehash: 263f591592063a45fdd5afdca4efdd75b5b915b6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339058"
---
# <a name="driver-tasks"></a>ドライバーでの処理
ドライバーによって実行される特定のタスクは次のとおりです。  
  
-   データソースへの接続と切断。  
  
-   ドライバーマネージャーによってチェックされていない関数エラーを確認しています。  
  
-   トランザクションの開始これは、アプリケーションに対して透過的です。  
  
-   実行用のデータソースに SQL ステートメントを送信しています。 ドライバーは、ODBC SQL を DBMS 固有の SQL に変更する必要があります。これは、多くの場合、ODBC で定義されている、DBMS 固有の SQL を使用したエスケープ句の置換に限定されます。  
  
-   データソースとの間でのデータの送受信 (アプリケーションで指定されたデータ型の変換を含む)。  
  
-   DBMS 固有のエラーを ODBC SQLSTATEs にマップしています。
