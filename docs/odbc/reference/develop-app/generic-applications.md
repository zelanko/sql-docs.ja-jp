---
title: 汎用アプリケーション |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], generic applications
- interoperability [ODBC], levels
- generic applications [ODBC]
ms.assetid: dda2a3c4-76ef-40a6-b3a1-9e95bed61618
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 607676d5370f02ee1d39196bff9261bc897521ee
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305553"
---
# <a name="generic-applications"></a>汎用アプリケーション
汎用アプリケーションでは、ワークシートによってデータベースからデータが取得されるなど、ハードコーディングされたタスクが実行されることがあります。 また、ユーザーが SQL ステートメントを入力して実行できる汎用クエリアプリケーションなど、さまざまなユーザー定義タスクを実行する場合もあります。 一般的なアプリケーションとしては、さまざまな Dbms を使用する必要があり、これらの Dbms が事前にわかっているとは限りません。  
  
 そのため、汎用アプリケーションは相互運用可能である必要があります。 開発者は多くの選択肢を選択し、機能の相互運用性を犠牲にする必要があります。また、さまざまな機能をサポートするドライバーを想定したコードを記述する必要があります。 一般的なアプリケーションは、一般的な Dbms で動作するようにチューニングされていますが、ドライバー固有または DBMS 固有のコードが含まれることはほとんどありません。
