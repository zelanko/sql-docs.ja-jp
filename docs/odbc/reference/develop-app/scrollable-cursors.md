---
title: "スクロール可能なカーソル |Microsoft ドキュメント"
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
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
ms.assetid: 2c8a5f50-9b37-452f-8160-05f42bc4d97e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 07e868f5798e759a9b84e9c28d2c1fa82bb34c4f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="scrollable-cursors"></a>スクロール可能なカーソル
最新のスクリーン ベースのアプリケーションでは、ユーザーは、データを前後をスクロールします。 このようなアプリケーションでは、以前にフェッチした行を返すことは問題です。 1 つの可能性を開始、カーソル閉じてから、必要な行がカーソルに到達するまでの行をフェッチします。 別の方法としては、結果セットを読み取り、それをローカルにキャッシュおよびアプリケーションでのスクロールを実装するのにです。 どちらが小さい結果セットにのみ使用し、後者が可能な実装が困難です。 良いソリューションは、使用する、*スクロール可能なカーソルは、*後ろに移動し、結果セットに転送することができます。  
  
 A*スクロール可能なカーソル*は最新のスクリーン ベースのアプリケーションをユーザーがスクロール前後データでよく使用します。 ただし、アプリケーションはスクロール可能なカーソル順方向専用カーソルが、ジョブを実行していない場合にのみと使用スクロール可能なカーソルは順方向専用カーソルより通常高価です。  
  
 後方に移動する機能には、順方向専用カーソルに適していない質問を発生させます。 スクロール可能なカーソルが以前にフェッチされた行に加えられた変更を検出する必要がありますか。 その更新、削除、および新しく挿入された行を検出する必要がありますか。  
  
 結果の定義を設定するために、この質問が発生: 特定の条件に一致する行のセット: 行をチェックして、その条件に一致するかどうかも、状態はときに記載されていないかどうかの行含める必要があります、同じデータがフェッチされるたびにします。 以前の省略できるようになりますスクロール可能なカーソルの行が挿入または削除されますが、後者により更新されたデータを検出するかどうかを検出します。  
  
 変更を検出する機能があります便利ですが、場合がありますされません。 たとえば、会計アプリケーションには、すべての変更を無視するカーソル必要があります。ブックの分散では、カーソルが最新の変更内容を表示されている場合は実行できません。 その一方で、航空券予約システムがデータを最新の変更内容を表示するカーソル必要があります。このようなカーソルなしは、最新の航空券の可用性を表示するデータベースを継続的に再実行する必要があります。  
  
 さまざまなアプリケーションのニーズをカバーするには、は、ODBC は、次の 4 つのさまざまな種類のスクロール可能なカーソルを定義します。 これらのカーソルでは、経費の両方を変更し、結果に変更を検出する機能に設定します。 スクロール可能なカーソルが行への変更を検出できる場合に検出できることのみにこれらの行を更新しようとしたときに注意してください。現在フェッチされている行への変更がカーソルに通知する、データ ソースの方法はありません。 変更の可視性が、トランザクション分離レベルによっても制御されることにも注意してください。詳細については、次を参照してください。[トランザクション分離](../../../odbc/reference/develop-app/transaction-isolation.md)です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [スクロール可能なカーソルの種類](../../../odbc/reference/develop-app/scrollable-cursor-types.md)  
  
-   [スクロール可能なカーソルを使用します。](../../../odbc/reference/develop-app/using-scrollable-cursors.md)  
  
-   [相対パスと絶対スクロール](../../../odbc/reference/develop-app/relative-and-absolute-scrolling.md)  
  
-   [ブックマーク](../../../odbc/reference/develop-app/bookmarks-odbc.md)

